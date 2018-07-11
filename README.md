# Cryptodex
Shell script to install a [Cryptodex Masternode](http://cryptodexa.cx/) on a Linux server running Ubuntu 16.04.
***

## Installation:
```
wget -N https://raw.githubusercontent.com/zoldur/Cryptodex/master/cryptodex_install.sh
bash cryptodex_install.sh
```
***

## Desktop wallet setup

After the MN is up and running, you need to configure the desktop wallet accordingly. Here are the steps for Windows Wallet
1. Open the Cryptodex Core Wallet.
2. Go to RECEIVE and create a New Address: **MN1**
3. Send **10000** **CXD** to **MN1**. You need to send all 10000 in one single transaction.
4. Wait for 15 confirmations.
5. Go to **Tools -> "Debug console - Console"**
6. Type the following command: **masternode outputs**
7. Go to  ** Tools -> "Open Masternode Configuration File"
8. Add the following entry:
```
Alias Address Privkey TxHash Output_index
```
* Alias: **MN1**
* Address: **VPS_IP:PORT**
* Privkey: **Masternode Private Key**
* TxHash: **First value from Step 6**
* Output index:  **Second value from Step 6** It can be **0** or **1**
9. Click OK and exit the Wallet.
10. Open Cryptodex Core Wallet, go to **Masternode Tab**. If you tab is not shown, please enable it from: **Settings - Options - Wallet - Show Masternodes Tab**
11. Click **Update status** to see your node. If it is not shown, close the wallet and start it again.
10. Click **Start All** or **Start Alias**
11. If you are not able to see your **Masternode**, try to close and open your desktop wallet.
***

## Usage:
```
cryptodex-cli getinfo
cryptodex-cli masternode status
cryptodex-cli mnsync status
```
Also, if you want to check/start/stop **Cryptodex** , run one of the following commands as **root**:
```
systemctl status Cryptodex #To check the service is running.
systemctl start Cryptodex #To start Cryptodex service.
systemctl stop Cryptodex #To stop Cryptodex service.
systemctl is-enabled Cryptodex #To check whetether Cryptodex service is enabled on boot or not.
```
***

## Sentinel

**Sentinel** is installed in **/root/Cryptodex/sentinel** and added to **crontab** file.
Sentinel log file is **/root/Cryptodex/sentinel.log**
Test the config by running the following commands:
```
cd /root/Cryptodex/sentinel
./venv/bin/py.test ./test
SENTINEL_DEBUG=1 ./venv/bin/python bin/sentinel.py
```
***

## Donations:

Any donation is highly appreciated.

**BTC**: 32tAw218fqnPY1zdgZTEquM71aPViGLqAQ . 
**ETH**: 0x39d10fe57611c564abc255ffd7e984dc97e9bd6d . 
**LTC**: LXrWbfeejNQRmRvtzB6Te8yns93Tu3evGf

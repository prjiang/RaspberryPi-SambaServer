# RaspberryPi-SambaServer
## Install Samba
```
pi@raspberrypi:~ $ sudo apt-get insatll samba
```
<b>選擇 yes</b>，安裝額外套件將 DHCP 取得的 WINS 設定寫入 smb.conf。

<br>

## Setting Samba
設定 SambaServer 的密碼。
```
pi@raspberrypi:~ $ sudo pdbedit -a -u pi
```
編輯 SambaServer 的設定檔。
```
pi@raspberrypi:~ $ sudo nano /etc/samba/smb.conf
```
在設定檔最後加入以下設定。
```
[Pi]
	comment = Pi's home
	path = /home/pi
	read only = no
	guest ok = no
	browseable = yes
	create mask = 0644
	directory mask = 0755
```
存檔後，重啟Samba。
```
pi@raspberrypi:~ $ sudo service smbd restart
```

<br>

## Usage
於檔案總管的網址列輸入以下指令，即可透過網路芳鄰讀取或寫入 Raspberry Pi 中的目錄與檔案。
| System | Command |
| --- | --- |
| Windows | \\\IP |
| Linux | smb://IP/目錄 |
| Mac OS X | smb://IP/目錄 |

> 參考資料: [RASPBERRY PI 安裝 SAMBA 網路芳鄰伺服器共享 WINDOWS 及 LINUX 檔案](http://blog.s2u4o.com/education/self-study/software-settings/raspbiansamba/)

> 參考資料: [樹莓派 Raspberry Pi 設定 Samba 網路芳鄰分享檔案教學](https://blog.gtwang.org/iot/raspberry-pi/raspberry-pi-samba-setup-tutorial/)

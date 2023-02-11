# RaspberryPi_Server
若使用Raspberry PI架設網站伺服器，需安裝LAMP軟體組合包，
即包含: Linux Apaceh MySQL PHP

- MySQL
-- MySQL念成My Sequel，是開放原始碼的關聯式資料庫管理系統，由於效能高 成本高 可靠性高等優點，已成為目前最流行的資料庫系統
<p>This is a normal paragraph:</p>

1. 開機後更新軟體:
<pre><code>sudo apt-get update
sudo apt-get upgrade
sudo reboot
</code></pre>
2. 初始設定為動態IP位址，在此設為靜態IP位址，以避免重新開機後需再查閱IP位址問題。
3. 使用ipconfig取得目前的網路的IP Broadcast Net Mask等位址
4. 使用下令指令取得Gateway網址:
<pre><code>ip route show
</code></pre>
5. 切換到目錄/etc/network，使用文字編輯器開啟interfaces(須系統管理者權限):
<pre><code>cd /etc/network
sudo nano interfaces
</code></pre>
- 初始設定為:
<pre><code>auto lo
iface lo inet loopback

auto eth0
allow-hotplug eht0
iface eth0 inet manual
...
</code></pre>
- 請修改為固定IP位址並存檔
<pre><code>auto lo
iface lo inet loopback

auto eth0
allow-hotplug eht0
iface eth0 inet static
address 192.168.1.81
gateway 192.168.1.254
netmask 255.255.255.0
broadcast 192.168.1.255
...
</code></pre>
6. 重新開機:
<pre><code>sudo reboot
</code></pre>
7. 確認IP位址是否已固定:
<pre><code>ifconfig
</code></pre>
8. 使用個人電腦測試Raspberry PI的網路連線狀態:
<pre><code>ping 192.168.1.81
</code></pre>

## Putty遠端控制
1. 確認Raspberry PI的SSH已開啟，請先進行下列設定:
<pre><code>sudo raspi-config
</code></pre>
- 於Advanced Options中選取SSH，並點選Enable:
2. 個人電腦端下載與安裝Putty軟體
3. 執行Putty，於Host Name(IP address)鍵入Raspberry PI的IP位址;接著按Open
4. 第一次連線會有安全考量，點選Yes
5. 將會開啟文字視窗，鍵入使用者名稱與密碼登入即可開始進行遠端控制

## 伺服器
1. 開機後更新軟體:
<pre><code>sudo apt-get update
sudo apt-get upgrade
sudo reboot
</code></pre>
2. 安裝LAMP組合包:
<pre><code>sudo apt-get install apache2
sudo apt-get install php5
sudo apt-get install mysql-client mysql-server
</code></pre>

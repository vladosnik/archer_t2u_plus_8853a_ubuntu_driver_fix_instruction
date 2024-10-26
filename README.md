# archer_t2u_plus_8853a_ubuntu_driver_fix_instruction
Archer T2U Plus 8853A - T2U PLUS adapter Driver fix instruction linux Ubuntu 18.04.6 LTS
============================================================
```
Model: Archer T2U Plus
IC: 8853A-T2UPLUS
FCC ID: TE7T2UPLUS
MADE IN CHINA
```

problem: wifi not working at fresh install Ubuntu 18.04.6 LTS

solution Part 1 (driver installation for wifi adapter):
driver installation commands: 
```
git clone https://github.com/gnab/rtl8812au
mv rtl8812au /usr/src/8812au-4.2.3
sudo dkms add -m 8812au -v 4.2.3
sudo dkms build -m 8812au -v 4.2.3
sudo dkms install -m 8812au -v 4.2.3
```
solution Part 2 (fixing boot problems with plugged adapter, when adapter plugged in ubuntu can not startup properly):
```
sudo update-grub
sudo reboot
```
```
sudo nano /etc/default/grub
```
changes:
original line: 
```GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"```
replaced line: 
```GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbcore.autosuspend=-1"```


```
CTRL + SHIFT + S - save file
```
```
CTRL + X - close file
```

reboot command: 
```
sudo reboot
```


now it works perfect!

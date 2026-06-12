---
title: "Ubuntu14.04 gets stuck in a login loop"
date: 2018-08-01
forum: Desktop Environments
---

### Post by fengyegg on 2018-08-01
My Ubuntu14.04 gets stuck in a login loop. i can auto login to desktop  as root,but other user gets stuck in a login loop.
  
  (It is a dual-boot system ,windows 7 and Ubuntu14.04)
  
  One day i ```
`chmod -R 777 /usr/lib`
```,then i found sudo couldn't use anymore,so i enter recovery mode to fixed the problem
      
      ```

mount -o remount,rw /
sudo chmod 0755 /usr/lib
chmod 4755 /usr/lib/sudo/sudoers.so

``` 
     
  Then i found i could not login in anymore. 
  i add a new file  ```
`/etc/lightdm/lightdm.conf`

```  the content is:
     
      
```
     
 [SeatDefaults]
 autologin-user=root

```      


  reboot, i could autologin as root, and could see the default desktop,but when i try to login in as other user ,i just get stuck in a login loop in the login step.
  
  I try to add a new  user, still get stuck in a login loop(but i can login in terminal ,also ,i can still use windows system)
  
  i found a web page which might solve my problem ,[https://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop#](https://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop#),
  but  i try most of it , it didnt work for me :
      
     ```
 
      1. i try to install/reinstall lightdm and gdm,failed,
      2. i try to install  Nvidia and AMD/ATI graphics driver,  
      'sudo apt-get install nvidia-390' and 'sudo apt-get install fglrx',
      both failed because 'lib32gcc1 : Depends: gcc-4.9-base (= 4.9-20140406-0ubuntu1) but 4.9.3-0ubuntu1 is to be installed',
      I  try to install gcc-4.9-base,it shows too many dependence have to install/update 
      3. sudo apt-get -y install lubuntu-desktop and sudo apt-get -y install lxdm still get login loop
      4. chmod for Xauthority /tmp

```  
  what is the cause ? how can i solve it? Thanks!
  
  
  ps : There is another clue, the /var/log/cups/error_log grow rapidly ,
  the message is 
      
      
```
      
W [01/Aug/2018:00:38:14 +0800] Notifier for subscription 1 (dbus://) went away, retrying!
E [01/Aug/2018:00:38:14 +0800] Directory "/usr/lib/cups/notifier" has insecure permissions (044755/uid=0/gid=0).

```      


and i see memory usage grow too , but could not see witch process use it,why  cupsd use 90+% cpu?
    
    
    ```

Tasks: 186 total,   2 running, 184 sleeping,   0 stopped,   0 zombie
    %Cpu(s):  9.4 us, 16.0 sy,  0.0 ni, 74.3 id,  0.3 wa,  0.0 hi,  0.0 si,  0.0 st
    KiB Mem:  12183948 total, 12031564 used,   152384 free,     3780 buffers
    KiB Swap:  4071420 total,     8456 used,  4062964 free. 10761820 cached Mem


      PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
     2339 root      20   0   76868   3696   2652 R  99.8  0.0  55:52.53 cupsd       
       10 root      20   0       0      0      0 S   1.3  0.0   0:19.72 rcuos/2     
     2519 root      20   0  666088  22280  13220 S   1.0  0.2   0:01.31 gnome-term+ 
     1172 root      20   0  487632  51176  39124 S   0.7  0.4   0:05.67 Xorg        
     1971 root      20   0  286792   5032   3952 S   0.7  0.0   0:00.08 indicator-+ 
        7 root      20   0       0      0      0 S   0.3  0.0   0:04.42 rcu_sched 

```

---

### Post by Autodave on 2018-08-02
Did this happen suddenly or after an update or upgrade?

---

### Post by fengyegg on 2018-08-03
It happened after i `chmod -R 777 /usr/lib`, I did not update/upgrade at first when i start to try to fix the problem. When i followed the advice in [https://askubuntu.com/questions/2235...-a-login-loop#](https://askubuntu.com/questions/2235...-a-login-loop#), i did  try `sudo apt-get update` and `sudo apt-get -y dist-upgrade`[COLOR=#000000][FONT=Ubuntu Mono]

I decide to reinstall Ubuntu now.

Thank you! [/FONT][/COLOR]

---

### Post by QIII on 2018-08-03
Just to add this note:

Whoever suggested recursively changing the permissions on a system directory like that was outrageously wrong.  Even just changing the directory permissions is a terrible idea.  Don't do things like that.

---


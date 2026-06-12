---
title: "questions about grub"
date: 2011-10-28
forum: Desktop Environments
---

### Post by linux.girl on 2011-10-28
Hello everyone,

A few questions about grub: is grub supposed to appear before the OS loads? Or only when you have dual boot?

Is there a way to make sure grub always appears before the OS loads? It gets me nervous not to see grub, if one day something happens and I need it, I dont know how to get to it, so I would feel much better if it would always appear before OS loads. 

PS: I know that pressing shift should make grub appear, but it doesnt. 

Any suggestions?

linux.girl

---

### Post by vicshrike on 2011-10-28
Yes, it should appear before the OS loads.

---

### Post by linux.girl on 2011-10-28
Thanks! So mine is not loading, how do I fix it?

---

### Post by jack.b on 2011-10-28
> **linux.girl said:**
> Thanks! So mine is not loading, how do I fix it?

best way to learn what might be the problem is to check what is available, my script called bin, ls -oaF for most of the places programs are;
-----
$ cat /usr/pfs/bin/bin                                                                                                            
#    -n no newline                                                                                                                
                                                                                                                                  
# /KNOPPIX/etc/init.d/knoppix-autoconfig got working colors here                                                                  
                                                                                                                                  
# ANSI COLORS                                                                                                                     
"                                                                                                                                 
NORMAL=""                                                                                                                         
# RED: Failure or error message
RED=""
# GREEN: Success message                                                                                                          
GREEN=""                                                                                                                          
# YELLOW: Descriptions                                                                                                            
YELLOW=""                                                                                                                         
# BLUE: System messages                                                                                                           
BLUE=""                                                                                                                           
# MAGENTA: Found devices or drivers                                                                                               
MAGENTA=""                                                                                                                        
# CYAN: Questions                                                                                                                 
CYAN=""                                                                                                                           
# BOLD WHITE: Hint                                                                                                                
WHITE=""                                                                                                                          
                                                                                                                                  
echo                                                                                                                              
echo     "${RED}                                       /bin ------- 1 -*-"                                                        
ls -oaF --color=auto /bin/*$**                                                                                                    
echo                                                                                                                              
echo     "${CYAN}                                       /sbin ------ 2 -*-"                                                       
ls -oaF --color=auto /sbin/*$**                                                                                                   
echo                                                                                                                              
echo     "${YELLOW}                                      /usr/bin --- 3 -*-"                                                      
ls -oaF --color=auto /usr/bin/*$**                                                                                                
echo                                                                                                                              
echo     "${BLUE}                                       /usr/sbin -- 4 -*-"                                                       
ls -oaF --color=auto /usr/sbin/*$**                                                                                               
echo                                                                                                                              
echo    "${MAGENTA}                                       /usr/pfs/bin 5 -*-"                                                     
ls -oaF --color=auto /usr/pfs/bin/*$**                                                                                            
echo

------
then

$ bin grub                                                                                                                        
                                                                                                                                  
                                       /bin ------- 1 -*-                                                                         
ls: cannot access /bin/*grub*: No such file or directory                                                                          
                                                                                                                                  
                                       /sbin ------ 2 -*-                                                                         
-rwxr-xr-x 1 root 375 2011-09-26 14:26 /sbin/grub-install*                                                                        
-rwxr-xr-x 1 root 466 2011-09-26 14:26 /sbin/update-grub*

                                      /usr/bin --- 3 -*-
-rwxr-xr-x 1 root   5572 2011-04-27 06:29 /usr/bin/grub-bin2h*                                                                    
-rwxr-xr-x 1 root  22108 2011-04-27 06:29 /usr/bin/grub-editenv*
-rwxr-xr-x 1 root 159160 2011-04-27 06:29 /usr/bin/grub-fstest*
-rwxr-xr-x 1 root  18136 2011-04-27 06:29 /usr/bin/grub-mkelfimage*
-rwxr-xr-x 1 root  18228 2011-04-27 06:29 /usr/bin/grub-mkfont*
-rwxr-xr-x 1 root  88172 2011-04-27 06:29 /usr/bin/grub-mkisofs*
-rwxr-xr-x 1 root  26448 2011-04-27 06:29 /usr/bin/grub-mkpasswd-pbkdf2*
-rwxr-xr-x 1 root  13896 2011-04-27 06:29 /usr/bin/grub-mkrelpath*
-rwxr-xr-x 1 root   5926 2011-04-27 06:28 /usr/bin/grub-mkrescue*
-rwxr-xr-x 1 root  30660 2011-04-27 06:29 /usr/bin/grub-script-check*

                                       /usr/sbin -- 4 -*-
-rwxr-xr-x 1 root 148432 2011-09-26 14:26 /usr/sbin/grub*                                                                         
-rwxr-xr-x 1 root    153 2011-09-26 14:26 /usr/sbin/grub-floppy*
-rwxr-xr-x 1 root  16528 2011-09-26 14:26 /usr/sbin/grub-install*
-rwxr-xr-x 1 root   2312 2011-09-26 14:26 /usr/sbin/grub-md5-crypt*
-rwxr-xr-x 1 root   6910 2011-04-27 06:28 /usr/sbin/grub-mkconfig*
-rwxr-xr-x 1 root  26324 2011-04-27 06:29 /usr/sbin/grub-mkdevicemap*
-rwxr-xr-x 1 root 163544 2011-04-27 06:29 /usr/sbin/grub-probe*
-rwxr-xr-x 1 root   1461 2011-09-26 14:26 /usr/sbin/grub-reboot*
-rwxr-xr-x 1 root   3178 2011-09-26 14:26 /usr/sbin/grub-set-default*
-rwxr-xr-x 1 root   2473 2011-09-26 14:26 /usr/sbin/grub-terminfo*
-rwxr-xr-x 1 root  42821 2011-09-26 14:26 /usr/sbin/update-grub*

                                       /usr/pfs/bin 5 -*-
ls: cannot access /usr/pfs/bin/*grub*: No such file or directory                                                                  
  all kinds of grub stuff, but screamingly horrible  understand the  grub-probe --help, to the rescue is search
google[  tutorial grub-probe ],
choose thew 1st GRUB 2 bootloader - Full tutorial
[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)

hope this is helpful

jack

---

### Post by linux.girl on 2011-10-28
wow, thanks a lot, will definitely check it out.

I also found another possible solution here:

[http://ubuntuforums.org/showthread.php?t=1302743](http://ubuntuforums.org/showthread.php?t=1302743)

I think it turns out my hgrub hidden timout is set to 0 and thats why grub is not loading. I am not a 100% sure yet, but almost, that this is the case.

In any event, learned a lot from your post, so thanks again!

---

### Post by haqking on 2011-10-28
the grub menu which i think you are referring to does not always show, it depends.

As you suggested it is likely to be set to 0.

read here for more info on grub [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

you can edit your grub with

```
gksudo gedit /etc/default/grub
```

or editor of choice such as nano, if you use gedit make sure you use gksudo and not sudo (it is for graphical apps_

---

### Post by grahammechanical on 2011-10-28
A Ubuntu install always installs Grub. It is the boot loader. It loads the Linux image that is the OS.

If you only have Ubuntu on the hard disk you will not see a Grub menu. It is not needed. But Grub is there and if Ubuntu is loading it is doing its job.

A couple of links:

Grub Basics
[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

Grub customizer
[http://ubuntuforums.org/showthread.php?t=1664134]("http://ubuntuforums.org/showthread.php?t=1664134")

I find Grub Customizer invaluable.

Regards.

---


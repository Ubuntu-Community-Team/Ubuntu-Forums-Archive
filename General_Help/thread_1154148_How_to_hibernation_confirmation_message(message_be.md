---
title: "How to: hibernation confirmation message(message before hibernate)"
date: 2009-05-09
forum: General Help
---

### Post by ~Las~ on 2009-05-09
Sometimes when im reading or watching a movie power saving function enables hibernation with out giving a notice...so i googled and only found this

[http://ubuntuforums.org/showthread.php?t=730072](http://ubuntuforums.org/showthread.php?t=730072)

But it was not enough for my need 

so i used it and add some function to cancel hibernate process..


1.  Open gconf-editor. Go to Apps->gnome-power-manager->lock
    uncheck hibernate. This will inhibit powermanager to lock your screen right after you click the hibernate button.(just as earlier thread)


2.made a copy of /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux as /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linuxa

3.Edited /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux as
```
#!/bin/sh
  getXuser() {                                                                                                                                                 
        user=`finger| grep -m1 ":$displaynum " | awk '{print $1}'`                                                                                           
        if [ x"$user" = x"" ]; then                                                                                                                          
                user=`finger| grep -m1 ":$displaynum" | awk '{print $1}'`                                                                                    
        fi                                                                                                                                                   
        if [ x"$user" != x"" ]; then                                                                                                                         
                userhome=`getent passwd $user | cut -d: -f6`                                                                                                 
                export XAUTHORITY=$userhome/.Xauthority                                                                                                      
        else                                                                                                                                                 
                export XAUTHORITY=""                                                                                                                         
        fi                                                                                                                                                   
}                                                                                                                                                            
                                                                                                                                                             
        for x in /tmp/.X11-unix/*; do                                                                                                                        
            displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`                                                                                                  
            getXuser;                                                                                                                                        
            if [ x"$XAUTHORITY" != x"" ]; then                                                                                                               
                export DISPLAY=":$displaynum"                                                                                                                                                                                                                                
                 pid=`pgrep -u "MY USERNAME" gnome-screensav`                                                                                                       
                 DBUS=`grep -z DBUS_SESSION_BUS_ADDRESS /proc/$pid/environ | sed -e 's/DBUS_SESSION_BUS_ADDRESS=//'`                                                                                                                                            
                ###HERE RUN ANY PROGRAM WHICH WILL DISPLAY YOUR MESSAGE ###
        beep  -l500 -r2 -f900        
(
echo "0" ; sleep 1
echo "# 10 Sec to Hibernate" ; 
echo "10" ; sleep 1
echo "# 9 Sec to Hibernate" ; 
echo "20" ; sleep 1
echo "# 8 Sec to Hibernate" ; 
echo "30" ; sleep 1
echo "# 7 Sec to Hibernate" ; 
echo "40" ; sleep 1
echo "# 6 Sec to Hibernate" ; 
echo "50" ; sleep 1
echo "# 5 Sec to Hibernate" ; 
echo "60" ; sleep 1
echo "# 4 Sec to Hibernate" ; 
echo "70" ; sleep 1
echo "# 3 Sec to Hibernate" ; 
echo "80" ; sleep 1
echo "# 2 Sec to Hibernate" ; 
echo "90" ; sleep 1
echo "# 1 Sec to Hibernate" ; 
echo "100" ; sleep 1
) |
zenity --progress \
--title="Hibernate" \
--auto-close \




if [ "$?" = 0 ] ; then
sh /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linuxa & sudo -u "MY USERNAME" gnome-screensaver-command --lock 


fi


                                                                       
             fi                                                                                                                                               
        done                                                                                                                           


```I hope this would help anyone faces the same trouble as me.You have to replace "MY USERNAME" to your current login user name.(so im not sure if it works on other users)This will give a 10sec countdown to hibernate before it does with the option of cancel button.It also locks the screen wehen it resumes from hibernate..
P.S.
Im a nubee so if I'we done something wrong pls correct me..This is my first post

---

### Post by keithweddell on 2009-05-09
Not a problem that I've come across but nice solution.  I'll file for future use.  First post too?

Keith

---

### Post by ~Las~ on 2009-05-09
Ya its my first..:).I started using Ubuntu from Jan this year and every day Im loving it more...

---


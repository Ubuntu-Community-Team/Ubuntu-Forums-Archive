---
title: "xfce desktop icons"
date: 2006-11-26
forum: Desktop Environments
---

### Post by sawjew on 2006-11-26
I have just installed xubuntu desktop again (I used it for a while when Edgy was still beta) and when I used it before it had the desktop icons as shown here [http://thunar.xfce.org/images/thunar-xfdesktop-rc1.png](http://thunar.xfce.org/images/thunar-xfdesktop-rc1.png).  This picture comes from here [http://thunar.xfce.org/news.html]("http://thunar.xfce.org/news.html")

When I installed it this time they are not there. Does anyone know how to put these icons back on the desktop?  I'm sure it's something simple but I can't find out what.

---

### Post by CoolHand on 2006-11-26
> **sawjew said:**
> I have just installed xubuntu desktop again (I used it for a while when Edgy was still beta) and when I used it before it had the desktop icons as shown here [http://thunar.xfce.org/images/thunar-xfdesktop-rc1.png](http://thunar.xfce.org/images/thunar-xfdesktop-rc1.png).  This picture comes from here [http://thunar.xfce.org/news.html]("http://thunar.xfce.org/news.html")

When I installed it this time they are not there. Does anyone know how to put these icons back on the desktop?  I'm sure it's something simple but I can't find out what.

Under Settings/Desktop on the Behavior tab you can turn on or off desktop icons and set the types of icons.  As for those individual icons I don't know if they are default or if you will have to add them but I think the default to add an icon is a right click on the desktop and some option there.

---

### Post by sawjew on 2006-11-26
I already have desktop icons turned on and set to launchers.  I can add the filesystem and Home icons easily enough but the trash icon is a trash can with all the normal trash functionality and I don't know how to add that.

---

### Post by simonishe on 2006-12-06
Hi, 

 I just wanted to know if you got things to work with the trash can.
I have the exact same problem on my desktop (xubuntu edgy) : although the trash can appears on another debian etch testing installation I've done, it's not there on the xubuntu desktop. Both have (almost) the same versions, though.

 Really can't figure this out... Any help greatly appreciated..

---

### Post by sawjew on 2006-12-06
It seems the version of xfce on Edgy doesn't include the desktop icons.  It's probably the xfdesktop version.  I had them before but I realised that was on Dapper when I upgraded using the xfce installer.  That had the icons but caused me a lot of problems and I ended up reinstalling the system.

I got the icons on my Edgy system by adding the Debian unstable repositories and manually upgrading all the xfce packages with synaptic.  I then commented out the debian repositories and went back to Ubuntu only repositories and so far so good, I have had no problems.  The only problem now is that the suspend and hibernate buttons are not there in the logout window in the debian version of xfce.

Apart from that everything is fine and I have xfce 4.4rc3 installed.:-D

---

### Post by simonishe on 2006-12-06
Thanks a lot for your answer!
I kind of figured out the fact that this problem might actually be a new "feature" :-) ([http://ubuntuforums.org/printthread.php?t=284446](http://ubuntuforums.org/printthread.php?t=284446))

I think I'll probably do the same as you did, I'll put the debian packages in  xubuntu instead.

As for the shutdown issue in debian, this might help:
"To be able to shutdown the computer, you must be listed
in the systems sudoers file, in particular, you must be allowed to execute
$libexecdir/xfsm-shutdown-helper as user root (where $libexecdir is the
libexec subdir in the prefix you installed xfce4-session, for example
/usr/local/libexec)."  (xfce4-session doc)
 I haven't tried it yet, but I definitely will.

Alright, then.

---

### Post by simonishe on 2006-12-06
The shutdown issue is solved!

Just add

{your username}    ALL= NOPASSWD: /usr/sbin/xfsm-shutdown-helper

to the /etc/sudoers file (with the visudo command)

---

### Post by CoolHand on 2006-12-07
I think you are right about the addition of a feature.  There is a trashcan widget for the panel now.

You may be able to recreate the desktop icon though.  Have you tried making a launcher/link to "trash:///" ?  That is the way the trash location shows up in the thunar location bar.  Don't know if it will give you all the functionality but it might.  You may have to experiment.  Maybe a link to thunar with the argument of "trash:///".

---

### Post by simonishe on 2006-12-07
OK, I have the feeling there's really no way to have the trash icon on the desktop, so I've made a little script that emulates it.

 Just make the script executable, put in somewhere in your path (you don't have to, but I guess it'll be cleaner in /usr/local/bin, huh?), and launch it once, it will install itself.
 If you invoke it with "--kill-daemon", the icon will be able to update itself on the desktop not only when you open the trash can on the desktop, but also when you close it (e.g you might want to empty it sometimes...)
 If you don't like the name "Corbeille" (it's French for "Trash Can"), just modify the variable "IconName" in the script before you install it.

This script is probably crappy, well, for me it's good enough, if anyone wants to make improvements, it will be much appreciated (please send a patch :-)


```



#!/bin/bash                                                                                         
                                                                                                    
# Petite corbeille de remplacement pour le bureau xfce                                              
# 07/12/2006 (c) Simon Adda-Reyss                                                                   
                                                                                                    
# 0.0.20061207                                                                                      
                                                                                                    
# Usage : simxftrash [--kill-daemon] [fichier1] [fichier2...]                                       
#            --kill-daemon : kills any running instances of                                         
#               thunar, so that trash icon gets updated                                             
#         simxftrash                                                                                
#            Ouvre ou s'auto-installe                                                               
                                                                                                    
PROG="`readlink -f \"$0\"`"                                                                         
IconName=Corbeille                                                                                  
Comment=Corbeille                                                                                   
FileName="`echo \"$IconName\" | sed -e 's/ /_/g' |\                                                 
   tr '[:upper:]' '[:lower:]'`"                                                                     
LANCEUR=`readlink -f ~/Desktop`                                                                     
LANCEUR="$LANCEUR/$FileName.desktop"                                                                
                                                                                                    
if [ "x$1" = "x--kill-daemon" ] ; then                                                              
 KD=1                                                                                               
 PROG="$PROG --kill-daemon"                                                                         
 shift                                                                                              
else                                                                                                
 KD=0                                                                                               
fi                                                                                                  
                                                                                                    
if [ ! -e "$LANCEUR" ] ; then  
 cat <<EOF >"$LANCEUR"                                                                              
[Desktop Entry]                                                                                     
Name=$IconName                                                                                      
Exec=$PROG %F                                                                                       
Terminal=false                                                                                      
StartupNotify=false                                                                                 
Comment=$Comment                                                                                    
Icon=gnome-stock-trash                                                                              
EOF                                                                                                 
exit                                                                                                
fi                                                                                                  
                                                                                                    
CheckFull () {                                                                                      
plein="`ls ~/.local/share/Trash/files`"                                                             
if [ -s "$LANCEUR" ] ; then                                                                         
 if [ -n "$plein" ] ; then                                                                          
  sed -i -e '/^Icon=gnome-/s/^..*$/Icon=gnome-stock-trash-full/' \                                  
   "$LANCEUR"                                                                                       
 else                                                                                               
  sed -i -e '/^Icon=gnome-/s/^..*$/Icon=gnome-stock-trash/' \                                       
   "$LANCEUR"                                                                                       
 fi                                                                                                 
fi                                                                                                  
}                                                                                                   
                                                                                                    
if [ -e "$1" ] ; then                                                                               
  mv "$@" ~/.local/share/Trash/files                                                                
  CheckFull                                                                                         
else                                                                                                
 CheckFull               
                                                                                                    
 DAEMONKANA="`ps -C Thunar -o user,cmd | sed '1d' | \                                               
 grep -e \"$USER\" | grep -e \"--daemon\"`"                                                         
                                                                                                    
 if [ -n "$DAEMONKANA" ] ; then                                                                     
  if [ $KD -eq 1 ] ; then                                                                           
   thunar -q                                                                                        
  else                                                                                              
   echo "Thunar already present, icon might not update itself"                                      
  fi                                                                                                
 fi                                                                                                 
                                                                                                    
 thunar trash://                                                                                    
                                                                                                    
 CheckFull                                                                                          
fi

```

---

### Post by rsilva4 on 2007-02-22
I was trying to remove the trash/home/filesystem icons from the desktop and in the Desktop Settings window i find an icon that says help :o  , so lets click it, and i found out this:

> Extra File Icons

    In addition to file and launcher icons, xfdesktop can also display icons for removable volumes plugged into your computer. It can also display an icon for your filesystem root, home directory, and trash can. By default, these are all enabled, but can be disabled via hidden options. Create or edit the file $XDG_CONFIG_HOME/xfce4/desktop/xfdesktoprc and add something similar to the following:

    ```
[file-icons]
    show-filesystem=true
    show-home=true
    show-trash=true
    show-removable=true
```
              

    To disable that particular feature, change the "true" to "false" and save the file. If an entry is omitted, it defaults to "true". Restart xfdesktop for the changes to take effect. 


Well after all it's quite simple, btw my $XDG_CONFIG_HOME is /etc/xdg/ and i actually have to create the file :D, one other thing is that i'm running the Xubuntu feasty alpha release

---

### Post by simonishe on 2007-02-22
thanks a lot, that sounds great! 

Unfortunately, it looks like it doesn't work with xfce<4.4.0...
But it's a nice feature in the new version anyway!

---

### Post by kerry_s on 2007-02-22
sudo mousepad /etc/xdg/xfce4/desktop/xfdesktoprc

It's there, i'm using 4.4.0.

---


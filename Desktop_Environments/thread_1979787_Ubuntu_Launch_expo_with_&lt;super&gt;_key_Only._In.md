---
title: "Ubuntu: Launch expo with &lt;super&gt; key Only. Instead of &lt;super+s&gt;"
date: 2012-05-14
forum: Desktop Environments
---

### Post by animehunter123 on 2012-05-14
Hello,

Thank you for your help.

===============
Question: How can you launch Expo in Ubuntu12.04 by using the <super> by itself?
===============


I would like to launch the Expo view with only the <super> key. I know we can use ccsm to change the <super> key for unity, so I changed it to Shift+Ctrl+<super>

How can we change the Expo View Launcher from <super>+s to <super>. It doesnt seem to work for me in compiz. Can anyone provide guidance?

Thank you so much!:popcorn:



Here is my system information:

bobmiller@ubuntubob:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION=&quot;Ubuntu 12.04 LTS&quot;

bobmiller@ubuntubob:~$ uname -a
Linux ubuntubob 3.3.4-030304-generic #201205011755 SMP Tue May 1 01:56:36 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by animehunter123 on 2012-05-15
Sorry to bump this thread, but does anyone have any ideas? I want to launch expo to show all my windows but only via using the  key

---

### Post by IWantFroyo on 2012-05-15
This is because the dash is already controlled by the Super key. I don't think there's an option to change that in CCSM, though.

I suggest using the Ctrl-Alt-Arrowkey approach to switching workspaces for now.

---

### Post by animehunter123 on 2012-05-15
Thanks for the tip. Yes Ctrl Alt is fine, but I was wondering if the  key can work. Setting it via ccsm to any other key like F9 works fine, but I really need it to use the super key.   Ideas? Guidance? Thanks so much!

---

### Post by animehunter123 on 2012-05-16
I wonder if Ubuntu/Unity/Shell has a Hook that still holds onto the  key, even if you disable using it via compiz or Unity Settings.  Still playing around with this...     Does anyone know how to make the Expo plugin to show your workspaces work with the  key?

---

### Post by animehunter123 on 2012-05-21
I tried disabling unity and switching to xfce or kde; but the behaviour is the same.    Does anyone know how to launch EXPO to view your workspaces from the command-line or via the SUPER Key (not any other key)?

---

### Post by animehunter123 on 2012-05-28
Does anyone know how to do this? Please help...

---

### Post by gnusci on 2012-05-28
Intall GConf-Editor

$ sudo apt-get install gconf-editor

Run it, Super+A search by "gconf"

Form the menu "Edit" click "Find", and search for "expo_key", check "Serach also in key name"

You will find the lines:

/apps/compiz-1/plugins/expo/screen0/options/expo_key
/apps/compizconfig-1/profiles/Default/plugins/expo/screen0/options/expo_key

Then you need to customize expo_key value.

---

### Post by animehunter123 on 2012-05-28
Thank you very much. This information worked but did not succeed. Did I do something wrong: 
 
 Here is what i did: 

 0) Used Unity Settings Control Panel to set Unity Menu to Ctrl+Shift+Super. This works fine. Now, lets try and map Super to just launch expo. 
 1) sudo apt-get install -y gconf-editor 
 2) gconf-editor & 

   3) Searched and found expo_key entries (4 lines below): 
 /schemas/apps/compiz-1/plugins/expo/screen0/options/expo_key 
 /apps/compiz-1/plugins/expo/screen0/options/expo_key 
 /apps/compizconfig-1/profiles/Default/plugins/expo/screen0/options/expo_key 
 /schemas/apps/compiz-1/plugins/expo/screen0/options/expo_key 
 

 4) Changed all 4 entries of "expo_key" from "super s" to "super". 
 5) Rebooted machine. Pressed  super (the windows key) and nothing happened. If I press super + s, then it launches expo. What did I do wrong :(  
 -Ubuntu 12.04  


       > **gnusci said:**
> Intall GConf-Editor

$ sudo apt-get install gconf-editor

Run it, Super+A search by &quot;gconf&quot;

Form the menu &quot;Edit&quot; click &quot;Find&quot;, and search for &quot;expo_key&quot;, check &quot;Serach also in key name&quot;

You will find the lines:

/apps/compiz-1/plugins/expo/screen0/options/expo_key
/apps/compizconfig-1/profiles/Default/plugins/expo/screen0/options/expo_key

Then you need to customize expo_key value.

---

### Post by gnusci on 2012-05-29
Try changing the root settings

gksudo gconf-editor

---

### Post by animehunter123 on 2012-05-29
Hello,  I tried again with gksudo gconf-editor as local user and as root and still cannot map Expo to the super key. Any other ideas? Thanks so much for your help

---

### Post by gnusci on 2012-05-29
I think the problem you have it is that the <Super> is being used by another shortcut. If you search for "<Super>" in gconf-editor you will fine this two lines:

/apps/compiz-1/plugins/unityshell/screen0/options/show_launcher
/apps/compizconfig-1/profiles/Default/plugins/unityshell/screen0/options/show_launcher

You may need to change that too, if you want to use it for another purpose.

---

### Post by animehunter123 on 2012-05-30
Hello, 
    
  Thank you for your advice. Unfortunately it did not work. After changing the 'expo_key' to SUPER, I then searched for 'show_launcher' which was set to SUPER.    
 I changed:  /apps/compiz-1/plugins/unityshell/screen0/options/show_launcher  to SUPER ALT L  but i still cannot launch expo with the super key.      
 Can you try and do it? I made a vm from scratch of default ubuntu 12.04 and repeated and the vm did the same exact behaviour.    
    
How can I launch expo with just the SUPER  key? Thank you so much.

---

### Post by animehunter123 on 2012-06-06
Does anyone know how to do this? I need to launch Expo via the super key (windows key). Please help.):P

---


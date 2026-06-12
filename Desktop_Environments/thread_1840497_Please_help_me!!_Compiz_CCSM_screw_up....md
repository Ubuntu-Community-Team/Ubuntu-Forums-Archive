---
title: "Please help me!! Compiz CCSM screw up..."
date: 2011-09-07
forum: Desktop Environments
---

### Post by SMOKEY989 on 2011-09-07
Ubuntu 11.04

Hi

It seems i have completely screwed up Ubuntu mode 'Ubuntu', though classic mode seems to be fine.  Basically I've installed Compiz advanced (CCSM) changed settings and completely lost track of what I have done.  Stupidly in the process of trying to uninstall CCSM I got rid of unity 3.8.16ubuntu~natty1.  Ive tried reinstalling unity CCSM but hasn't worked.  The attached image gives you an idea what the problem is, it looks like the desktop has been stretched and zoomed, its really frustrating. 

As you can probably tell I am new to Linux UBuntu so any help will be really appreciated.  

thanks.

---

### Post by ajgreeny on 2011-09-07
In terminal run the command ```
gconftool-2 --recursive-unset /apps/compiz
``` followed by ```
unity --reset
``` then finally ```
sudo apt-get install ubuntu-desktop
``` to get everything back that may have been uninstalled.

---

### Post by SMOKEY989 on 2011-09-07
Ajgreeny thanks for your suggestions, unfortunately the weird screen error is still there. 

Here's the output code from each of your suggestions! (i ran a second time as i forgot to copy the code first time round).

gconftool-2 --recursive-unset /apps/compiz
No output

unity --reset
```
david@david-VGN-NW20EF-S:~$ unity --reset
Traceback (most recent call last):
  File "/usr/bin/unity", line 198, in <module>
    reset_unity_compiz_profile ()
  File "/usr/bin/unity", line 83, in reset_unity_compiz_profile
    if current_profile_gconfvalue.get_string() == 'unity':
AttributeError: 'str' object has no attribute 'get_string'
```


sudo apt-get install ubuntu-desktop

```
david@david-VGN-NW20EF-S:~$ sudo apt-get install ubuntu-desktop
[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-desktop is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.38-8-generic linux-headers-2.6.38-8
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

The final output may be a little bit different as i re-ran it to get the output.  I havr'nt got a clue why my screen is screwed up.  I'd reinstall but that looks like a complete pain!

Any help will be appreciated!

---

### Post by wildmanne39 on 2011-09-07
Hi, try this way please:
And just copy and paste the commands into the terminal.
These commands to reset all the settings in compiz.
```
gconftool-2 --recursive-unset /apps/compiz
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1

```
Then
```
Unity --reset
```
Let it run for about three minutes then restart your computer and see if that fixes your problem.
Thank you

---

### Post by SMOKEY989 on 2011-09-08
Thanks for this, I will give it a go tonight, I'm in work ay the moment.  Does it matter what mode I run this in?

Regards, David

---

### Post by ajgreeny on 2011-09-08
I am just wondering if the error message you got from the unity --reset command is a result of some bits of unity having been removed.

Try running ```
sudo apt-get install --reinstall ubuntu-desktop
``` this time before the unity --reset command, as that will make sure everything is installed that is in the default ubuntu installation.  That was my fault for not thinking about the **--reinstall** option being needed.

---

### Post by wildmanne39 on 2011-09-08
Hi, I do not remember which error messages you get from unity --rest but there are a lot and you just ignore them and after about three minutes you can restart your computer and it should work.

I myself have used unity reset at least twice.
Thank you

---

### Post by SMOKEY989 on 2011-09-08
Just before i restart my computer this is the output from running   unity --reset.  I don't know if this seems right! Hopefully!  I've ran this in classic mode too, not 'ubuntu' mode which i am having the problems with.

```
david@david-VGN-NW20EF-S:~$ unity --reset
Traceback (most recent call last):
  File "/usr/bin/unity", line 198, in <module>
    reset_unity_compiz_profile ()
  File "/usr/bin/unity", line 83, in reset_unity_compiz_profile
    if current_profile_gconfvalue.get_string() == 'unity':
AttributeError: 'str' object has no attribute 'get_string'
```

---

### Post by wildmanne39 on 2011-09-08
Hi, if you click on your username and go to the bottom of the page at the log in screen can you choose the one that says just ubuntu?
Thank you

---

### Post by SMOKEY989 on 2011-09-08
thanks Wildman, i know that part (one of few things at the moment ha), should i have run this in ubuntu mode then?

thanks for your help by the way, its greatly appreciated

---

### Post by wildmanne39 on 2011-09-08
Hi, yes it is usually done in ubuntu or unity, have never heard of it being done in classic mode, also from unity or ubuntu as it is called you can do this to get a terminal when it is not working right.

Open a terminal by hitting ctrl+alt+t or alt+f2, if  one of those key combination does not open the terminal try ctrl+alt+f1 thru f6. Then type this command in terminal to reset unity. 
```
unity --reset
```
You will still get many errors as I said I do not remember the exact ones there are several, just let it run for about three minutes then restart your computer, if you just tap your power button it should bring up a window to restart your computer if you are still in the unity desktop.
Thank you

---

### Post by SMOKEY989 on 2011-09-08
Woo hoo!! it's back to normal, well kind of...  The only things missing is the launcher bar on the left and dark grey title bar at the top which shows battery, active window, wireless connectivity.  DO you kjnow how get these back.  I'll leave you alone after that I promise ha ha!!

I will certainly be supporting you for your ubuntu membership, regards David.

---

### Post by wildmanne39 on 2011-09-08
Hi, there a a couple of things we can try, first do like ajgreeny mentioned and run this command please.
```
sudo apt-get install --reinstall ubuntu-desktop
```
You probably should restart your computer after you run the command and let us know if it works.
Thank you

---

### Post by SMOKEY989 on 2011-09-08
Can't believe this.  For some reason i can't open the terminal window now (ctrl alt  T).  Because i can't get access to the launcher bar etc this is the only way i know of.  I also haven't reinstalled the desktop.

---

### Post by wildmanne39 on 2011-09-08
Hi, is this you tried to open the terminal?
> ctrl+alt+t
it has to be done just like that.

Is this a clean install or did you upgrade from an older version?
Thank you

---

### Post by SMOKEY989 on 2011-09-08
Yes that's what i've done, i've used that combination previously and it has been fine.  For some reason it was just when i restarted the computer after i reset unity and compiz.  The installtion of 11.04 was a fresh install by the way, not an upgrade!

thanks

---

### Post by wildmanne39 on 2011-09-08
Hi, minus all open windows then hit alt+f2 does that open the launcher or dash so you can click on the terminal?
Thank you

---

### Post by SMOKEY989 on 2011-09-08
HI WIldmanne

No didnt work unfortunately.  Should i try and reinstall ubuntu desktop in classic mode, restart and log back in to normal ubuntu mode? See if that works.

thanks

---

### Post by wildmanne39 on 2011-09-08
Hi, I do not think so, please try it this way ctrl+alt+f1 thru f6 and see if it drops you to the tty screen, if it does do it from there.
Thank you

---

### Post by SMOKEY989 on 2011-09-08
WIldmanne 

Thanks for that.  you are going to be sick and tired of me but when i get to the tty screen 

it has login: i have tried to enter the username i log in to ubuntu ie. david saunderson but keeps saying incorrect login.

sorry about this :-( its starting to frustate me, thanks for your patience  !!

---

### Post by wildmanne39 on 2011-09-08
Hi, when you first get there I believe you type your user name then it should let you type your password but you will not see your password on the screen then you should have root access to enter the command.
Thank you

---

### Post by SMOKEY989 on 2011-09-08
Got access to it now! I reinstalled ubuntu desktop and it hasn't brought the launcher and title bar back.  DO you think it is a good idea to start and reset unity and compiz again through tty?  Or is there anything i can try??

Thanks

---

### Post by wildmanne39 on 2011-09-08
Hi, lets try this, here is a link to check out.
[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)
Thank you

---

### Post by SMOKEY989 on 2011-09-12
A big thanks to [ajgreeny]("http://ubuntuforums.org/member.php?u=27747") & Wildmanne for all your help and guidance, it was greatly appreciated!

Cheers

---

### Post by wildmanne39 on 2011-09-13
Hi, your welcome!

---


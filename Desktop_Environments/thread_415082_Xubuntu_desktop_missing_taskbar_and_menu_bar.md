---
title: "Xubuntu desktop missing taskbar and menu bar"
date: 2007-04-20
forum: Desktop Environments
---

### Post by godrox on 2007-04-20
I have Xubuntu Edgy on an old Toshiba notebook and it was working fine for a while, but recently the desktop lost it's whole interface no apparent reason. It boots up just fine, the login screen appears, I login successfully but all it shows after that is my desktop background image and the files and folders I had sitting on my desktop. There's not taskbar at the bottom of the screen nor is there a menu bar at the top.

Here's what I've tried so far:
1. Rebooting lots of times hoping it'll come back.
2. Hitting ALT+F2 to bring up "Run program" and using that to run terminal commands, such as "sudo apt-get update" and "sudo apt-get install xubuntu-desktop" but that didn't do anything.
3. Using "Run program" box to open the Update Manager and installing all new updates.

I'd like to upgrade it to Feisty, but I'm thinking that maybe it should be in a functional state first.

Any ideas how to bring back the rest of Xubuntu's GUI?

---

### Post by mojoman on 2007-04-20
Well, you could try ALT+F2 and the punch in "xfce4-panel". That, I think, should get the panel, together with the menu, back again. It doesn't really solve the problem, it just restart the application BUT you could try to go to the menu and under "Settings -> Sessions and Startup" chose "automatically save sessions on logout". If it is something in some configuration file somewhere (though it beats me what) this might save the changes with the panel up and running. It's a long shot and probably won't do you any good but hey, at least it's for free!

/mojoman

ps: I'm running Xubuntu Feisty since a couple of days and so far it runs just fine (knock on wood...). ds.

---

### Post by godrox on 2007-04-20
Thanks mojoman! I'm at work right now, but will try it as soon as I get home.

---

### Post by godrox on 2007-04-20
> **mojoman said:**
> Well, you could try ALT+F2 and the punch in "xfce4-panel". That, I think, should get the panel, together with the menu, back again. It doesn't really solve the problem, it just restart the application BUT you could try to go to the menu and under "Settings -> Sessions and Startup" chose "automatically save sessions on logout". If it is something in some configuration file somewhere (though it beats me what) this might save the changes with the panel up and running. It's a long shot and probably won't do you any good but hey, at least it's for free!

/mojoman

ps: I'm running Xubuntu Feisty since a couple of days and so far it runs just fine (knock on wood...). ds.

Well, "xfce4-panel" brought back the menu bar and taskbar, thanks! However, when click on "Quit" to shutdown the computer, I get this message:

[B]Unable to quit session.
Quitting the session requires that Xfce's session manager (xfce4-session) is running, but it was not detected.  Please quit Xfce via another means.[/B]

So I do ALT+F2 again and try running "xfce4-session" which brings up the splash screen and then returns to my desktop. I still get the same error message when I click "Quit" though. Now what?

---

### Post by mojoman on 2007-04-21
Well, you could punch this into a terminal (opened within xfce4):

```
ps aux | grep xfce
```

That should give you an output of all processes connected to xfce4, complete with the owner of the process, the process id and some more info. Mine look like this. 

```
mojoman@jukejoint:~$ ps aux | grep xfce
mojoman   5501  0.0  0.0   3860   544 ?        Ss   08:20   0:00 /bin/sh /etc/xdg/xfce4/xinitrc -- /etc/X11/xinit/xserverrc
mojoman   5539  0.0  0.0  31264   616 ?        Ss   08:20   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session startxfce4
mojoman   5542  0.0  0.0  13092   680 ?        S    08:20   0:00 /usr/bin/dbus-launch --exit-with-session startxfce4
mojoman   5551  0.0  0.6 136268  6456 ?        S    08:20   0:00 /usr/bin/xfce4-session
mojoman   5572  0.0  1.4 198768 15156 ?        Ss   08:20   0:00 xfce-mcs-manager
mojoman   5577  0.0  1.2 158812 12328 ?        S    08:20   0:01 xfce4-panel --sm-client-id 117f000101000117672193800000051530001 --display :0.0
mojoman   5582  0.0  1.3 144684 13928 ?        S    08:20   0:00 /usr/lib/xfdesktop4/xfce4/panel-plugins/xfce4-menu-plugin socket_id 18874401 name xfce4-menu id 1 display_name Xfce Menu size 34 screen_position 1
mojoman   5583  0.0  1.0 144412 11224 ?        S    08:20   0:00 /usr/lib/xfce4-mixer/xfce4/panel-plugins/xfce4-mixer-plugin socket_id 18874425 name xfce4-mixer id 11767399125 display_name Volume Control size 34 screen_position 1
mojoman   5584  0.0  0.8 103576  8628 ?        S    08:20   0:00 /usr/lib/xfce4-netload-plugin/xfce4/panel-plugins/xfce4-netload-plugin socket_id 18874444 name netload id 11767399547 display_name Network Monitor size 34 screen_position 11
mojoman   5585  0.0  0.8 103584  8572 ?        S    08:20   0:00 /usr/lib/xfce4-systemload-plugin/xfce4/panel-plugins/xfce4-systemload-plugin socket_id 18874445 name systemload id 11767399406 display_name System Load Monitor size 34 screen_position 11
mojoman   5586  0.0  0.6 127992  6860 ?        S    08:20   0:00 /usr/lib/thunar/xfce4/panel-plugins/thunar-tpa socket_id 18874446 name thunar-tpa id 4 display_name Trash Applet size 34 screen_position 11
mojoman   5961  0.0  0.0   5024   812 pts/0    R+   08:59   0:00 grep xfce
```

You could try that and have a look if there are any processes that your xfce4 isn't running. If so, try to bring that process up (but the panel-plugins is something that I have added so don't bother about them).

Also, xfce4 is started by a file called xinitrc. Where it's located differs among distros and, I think, the manner in which xfce was installed but for Xubuntu it should be in /etc/xdg/xfce4/xinitrc. I had a look at it, hoping that I could see what processes it starts but I couldn't really make any sense of it because, well, I know jack-crap about bash-scripts. Anyway, try looking at the processes to start with and get back.

Good luck.
/mojoman

---

### Post by godrox on 2007-04-21
Thanks for your reply, mojoman! Here's my output:

```
tim       3811  0.0  0.1   1656   476 ?        Ss   10:04   0:00 /bin/sh /etc/xdg/xfce4/xinitrc
tim       3917  0.0  0.2   4480   724 ?        Ss   10:04   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session startxfce4
tim       3920  0.0  0.2   2528   616 ?        S    10:04   0:00 /usr/bin/dbus-launch --exit-with-session startxfce4
tim       3946  1.2  2.4  69004  6256 ?        S    10:04   0:00 /usr/bin/xfce4-session
tim       4056  0.7  1.7  72980  4604 ?        Ss   10:04   0:00 xfce-mcs-manager
tim       4317 14.8  5.2  82220 13400 ?        Ss   10:05   0:02 xfce4-terminal
tim       4337  0.0  0.2   2796   748 pts/0    R+   10:05   0:00 grep xfce

```

I really have no idea what any of this means, but it looks to me like xfce4-panel isn't starting automatically, but xfce4-session is even though my error message says it's not. Hmm....

Over on [this thread]("http://ubuntuforums.org/showthread.php?p=2434183") it's suggested to clear out ~/.cache/sessions and reboot from the terminal (sudo reboot). I'm not really sure what that means, so I tried running "clear out ~/.cache/sessions" from the terminal, but nothing really happened.

Thanks again for your help! I appreciate it!

---

### Post by godrox on 2007-04-21
I also found this [over here]("http://ubuntuforums.org/showthread.php?t=208528"), in case it helps:

> Well, I can quit - restart by giving "sudo shutdown -r now" at terminal. I also found out that the dialog mentioned in the previous post happens if you have restarted xfce4-panel by giving command "xfce4-panel" in the Run Program dialog, not if you have restarted it in terminal. Strange indeed. Can anybody explain why it matters how you restart the panel?

My above code is from a fresh reboot, by the way. I did NOT run xfce4-panel before running that query. I booted the computer, hit ALT+F2, ran "xcfe4-terminal" and then "ps aux | grep xfce" in the terminal and that's my output.

---

### Post by mojoman on 2007-04-21
Ok, as far as I can see you have all the essential processes running. My five first processes corresponds to your five first processes. Then I have xfce-panel running and you  don't. After that, I got five processes that are panel-plugins which you obviously don't have since you don't have a panel but since they are optional you don't need them either. You got xfce-terminal running and I don't, which is weird since I ran the command in that terminal but since I don't have a problem we're not going to dig into that ;) The last processes we both have and that's the "ps aux | grep xfce" commando.

So, apart from the panel I can't see that your xfce is lacking any vital processes whatsoever and yo can get that going xfce-panel. If you do, I assume it shows up with a "ps aux | grep xfce"?

Anyway, you could try what the quote says, i.e. starting xfce-panel with the terminal. Open a terminal and just punch in "xfce-panel" then try to restart the computer with the log-out button. If you already have xfce-panel running, kill it with this command 

```
kill ####
``` (where #### is the process number which you can find out with "ps aux | grep xfce") and then bring it up again by entering xfce-panel in the terminal. Then try to restart the computer with the logout button. If that doesn't work, restart it with "sudo shutdown -r now".

I feel I'm starting to grasp after straws here but give a  try and post back. 
/mojoman

---

### Post by godrox on 2007-04-21
Okay, I tried opening xfce4-panel through the terminal instead. The panel opened successfully, but the terminal gave this error part-way through the process:

```
(xfce4-battery-plugin:4469): libxfce4util-CRITICAL **: xfce_rc_write_entry: assertion `value != NULL' failed
```

Going through Applications --> Quit still gives me the same "Unable to quit session" error, but click the exit door icon in the menu bar brings this message: "Exit Xfce panel?" with cancel or quit as my options. That's a little weird. It used to bring me to the same logout/shutdown/reboot screen as Applications -> Quit.

I'm fixing up this computer to donate to a charitable cause, but the person who would take it is only in town for today and tomorrow, so I may just try to upgrade to Feisty and hope that overwrites any areas that are causing problems. Formatting and starting over isn't really an option because the CD-ROM drive is unreliable and only works intermittently, so installing from CD probably won't work. You think upgrading is a good option or will just cause more problems at this point?

---

### Post by mojoman on 2007-04-21
> **godrox said:**
> Okay, I tried opening xfce4-panel through the terminal instead. The panel opened successfully, but the terminal gave this error part-way through the process:

```
(xfce4-battery-plugin:4469): libxfce4util-CRITICAL **: xfce_rc_write_entry: assertion `value != NULL' failed
```

Going through Applications --> Quit still gives me the same "Unable to quit session" error, but click the exit door icon in the menu bar brings this message: "Exit Xfce panel?" with cancel or quit as my options. That's a little weird. It used to bring me to the same logout/shutdown/reboot screen as Applications -> Quit.

I'm fixing up this computer to donate to a charitable cause, but the person who would take it is only in town for today and tomorrow, so I may just try to upgrade to Feisty and hope that overwrites any areas that are causing problems. Formatting and starting over isn't really an option because the CD-ROM drive is unreliable and only works intermittently, so installing from CD probably won't work. You think upgrading is a good option or will just cause more problems at this point?

Either upgrading or re-installing the entire xfce-desktop would be worth a try. You could start with reinstalling xfce and if that doesn't work, upgrading to Feisty. You're running Edgy, right? I've never tried edgy myself, I went straight from Dapper to Feisty (with a clean installation). Edgy for me always seemed a little ... well, edgy. I don't think they had the development time on it that it needed but that's just my opinion. Let me know how it worked out.
/mojoman

---

### Post by Billi on 2007-07-09
If you can open the menu on the screen, then go to Setting/Autostarted Applications, (right under the Settings Manager on mine). Click Add, in the Command box put /usr/X11R6/bin/xfce4-panel and I just put xfce4-panel in the name box, I didn't bother with a description. Log out and then restart, you should have a panel now. I'm sure this isn't the correct way to do this, but I'm not very smart, so I have to do things the easy way. Hope this works for you.

Billi

---

### Post by myklee on 2007-11-12
Yes that worked for me also.

I worked it out for myself after reading the first page of this thread [did not realise there was 2x pages] so here is confirmation that Billi's procedure works.

My fiancee's session became slow/unresponsive during an epiphany browser session, so she pulled-the-plug. On restart she lost the xfce panel, now restored 100%

M.

---

### Post by Narcoblix on 2008-04-19
Hi, I'm running the downloaded ISO of Xubuntu, and I'm running it inside of Q, the QEMU emulator for mac (Intel based). It takes a very long time to boot, and when it finally comes up, there is no taskbar or menu bar. I wanted to try installing it onto one of the virtual hard drives I have set up. but the install app never runs, and neither do any of the other applications. I have tried to re-downloading the ISO image, but the problem persists. I really need some help! Does anyone have any experience with this?

---


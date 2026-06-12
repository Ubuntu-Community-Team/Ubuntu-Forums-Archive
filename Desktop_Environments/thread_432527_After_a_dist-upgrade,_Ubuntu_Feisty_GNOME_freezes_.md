---
title: "After a dist-upgrade, Ubuntu Feisty GNOME freezes for 70 seconds after login"
date: 2007-05-04
forum: Desktop Environments
---

### Post by darkmaster on 2007-05-04
So, the problem is simple. 
I dist-upgraded from edgy and in edgy all was fine. The dist-upgrade was fine too. 
Now that I'm on Feisty, after a Log-in in GNOME, the system freezes and the white "shadow" of a window in the upper left corner of the screen appears. Then, after 70 seconds or so, the login music starts and the window becomes visible. It's an error telling me that not all of the theme components could be loaded....
I have to whait another 10 seconds for the Ubuntu splash bar to disappear and Network manager, Battery tool and all the other tray icons to appear, finally. At this point, the system is somewhat usable, eccept the windows don't have the decorator, Metacity. The windows are witout upper bar: I can't even move them.

So I had an idea: started Beryl Manager and setted it to metacity and then restarted the window manager. This time metacity loaded. So, now, I have beryl-manager starting at boot to have the basic decorator around windows! That's ridiculous. Plus I don't know why does GNOME asks for so much time to log in and why there's that error. Without Beryl manager activated, metacity doesn't start alone. 

Plus, I know this is not a network manager issue (I read it in another post) because I deactivated it from autostart and nothing changed. Same for the battery utiliy. I don't know what to do anymore. It is a GNOME only problem because if I start a KDE session all is good. But I need to use Gnome of course, I don't like KDE. What can I do? Any help?

I think that being able to read a sort of terminal outpoot would help a lot but... I don't know how can I do it since I'm booting the graphical interface. Help please???

That's a really bad problem.

---

### Post by shizeon on 2007-05-04
I am having the same (if not very similar) issue after upgrading to feisty.  Still trying to troubleshoot.

---

### Post by shizeon on 2007-05-04
I think I am coming closer to an answer.  I ended up creating a new user account and when I login with that everything works great.  So, I'm guessing an issue with some config files.   See if creating a new user account gets you to the desktop okay.  If it does, then this might be the same issue.

---

### Post by shizeon on 2007-05-05
So my issue had something to do with something in my .gnome2_private folder.  Removing this made my login proceed like normal.  I think it might have something to do with the updated Evolution as that was really the only config file in there  Hope this helps someone.

---

### Post by darkmaster on 2007-05-06
Mine not. I tryed to move a series of configuration files and rebooted, not so much changed, at least, now, after the 70 second dela, Gnome boots normally and everything is loaded immediatly: windows manager, tray applications.... but at login, the system still freezes for 70 seconds and the message error saying it could start some of gnome theme features still appears. The last outpoot it says it received is:

> Did not receive a reply. Possible causes include: the remote application
did not send a reply, the message bus security policy blocked the reply,
the reply timeout expired, or the network connection was broken.

And the things I moved after the help of a friend of mine from my local LUG where:

```
$: gconftool-2 –shutdown
$: mkdir ~/backup
$: mv ~/.gconf* ~/backup
$: mv ~/.gnome* ~/backup
$: mv ~/.config ~/backup
$: mv ~/.local ~/backup
$: mv ~/.nautilus ~/backup
$: sudo reboot
```

Any idea? I also tryed to delete the folder shizeon was talking about. Nothing changed except I lost all of my evolution preferences.

---

### Post by shizeon on 2007-05-06
Have you tried logging in with a different 'new' user account?   If it works, then it points to a configuration in your account.  If you still see the same problem, then it is more than likely system related.  Either way, will be one step closer to solving.

System -> Administration -> Users and Groups -> Add User

---

### Post by darkmaster on 2007-05-06
> **shizeon said:**
> Have you tried logging in with a different 'new' user account?   If it works, then it points to a configuration in your account.  If you still see the same problem, then it is more than likely system related.  Either way, will be one step closer to solving.

System -> Administration -> Users and Groups -> Add User

I forgot to say it. I created a new user and tryed to log him in. No changes: same freeze. i also posted the bug in launchpad, hope they're gonna help :(

---

### Post by cdrom600 on 2007-05-06
I'm also having this problem.  I have to have the beryl manager autostart to load metacity, and even then it takes 70-100 seconds.  Creating a new user account and logging in does not show the issue, so I  assume it's a config file or login script issue somewhere.
Removing my .gnome2_private directory does nothing.

---

### Post by darkmaster on 2007-05-07
> **cdrom600 said:**
> I'm also having this problem.  I have to have the beryl manager autostart to load metacity, and even then it takes 70-100 seconds.  Creating a new user account and logging in does not show the issue, so I  assume it's a config file or login script issue somewhere.
Removing my .gnome2_private directory does nothing.

Please visit this launchpad page I opened:

[https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/112840](https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/112840)

And write there that you have this problem too. This is for everyone having this problem. Maybe that way they're gonna give us some attention :)

---

### Post by habicht on 2007-05-08
I only had to remove ~/.gnomerc
After that it worked fine!

---

### Post by darkmaster on 2007-05-08
> **habicht said:**
> I only had to remove ~/.gnomerc
After that it worked fine!

I don't even have this folder in my Home dir! How do I delete it :) ?
please, anyone with this problem, post in launchpad a reply to my submitted bug!

---

### Post by cdrom600 on 2007-05-08
> **habicht said:**
> I only had to remove ~/.gnomerc
After that it worked fine!
This works!  Thank you so much - I've been puzzling over this for weeks!
For the record, my ~/.gnomerc contained only the following line:
```
export WINDOW_MANAGER=~/.gnome-compiz-manager/openbox
```
Since I'm not using compiz, this probably tried to load a window manager which wasn't installed.  This makes sense.
Again, thank you.

---

### Post by darkmaster on 2007-05-08
Escuse me boys but this phantomatic gnomerec should be in the home folder? I don't have it, dammit. Still I don't understands what hangs my system up for more than a minute at startup!!! :mad:

---

### Post by klato on 2007-05-08
I'm pretty sure .gnomerc is a hidden file...if you are in Nautilus, try hittinhg Ctrl+H to view hidden files, and you should see it... (I'm at work right now so please bear with me =)  I'm also having this problem and am going to try it when I get home.

---

### Post by cdrom600 on 2007-05-08
It is a hidden file.  It's called ".gnomerc" and is located in your home directory (/home/*username* or just ~).  You can delete it by viewing hidden files in Nautilus and then finding and removing the ".gnomerc" file, but it's easier to just open a terminal and type:
```
$ cd
$ rm .gnomerc
```
FYI, any file or directory whose name begins with a dot (.gnomerc, .bashrc, .mozilla/) is hidden.

---

### Post by darkmaster on 2007-05-08
yeah, since it started with "." of course it is hidden but it is not in my home. I don't have such a folder. I was hoping it wa somewhere else.

---

### Post by klato on 2007-05-09
removing .gnomerc worked like a charm over here.  thanks!

---

### Post by darkmaster on 2007-05-10
> **klato said:**
> removing .gnomerc worked like a charm over here.  thanks!

Argh! Why don't I have this folder? My problem is obviously not related with this dammit... Aniway I'm happy that you solved your problem.

---

### Post by cdrom600 on 2007-05-10
> **darkmaster said:**
> Argh! Why don't I have this folder?
.gnomerc is a file, not a folder.  ~ refers to your home directory (/home/user/).  I don't know wheters this will help, but it might.

---

### Post by darkmaster on 2007-05-10
> **cdrom600 said:**
> .gnomerc is a file, not a folder.  ~ refers to your home directory (/home/user/).  I don't know wheters this will help, but it might.

Thanks for the reply. It is not in my home folder aniway. All the hidden files starting with "g" that are in my gnome folder are gtk and something else :(

---

### Post by darkmaster on 2007-05-13
Solved, it was a network related issue. After the upgrade to Feisty, the configuation of

/etc/network/interfaces

had been altered. Fixing this file made GNOMe boot normally.

---

### Post by Omegatron on 2007-05-16
> **darkmaster said:**
> Solved, it was a network related issue. After the upgrade to Feisty, the configuation of

/etc/network/interfaces

had been altered. Fixing this file made GNOMe boot normally.

What did you change about that file?

---

### Post by darkmaster on 2007-05-16
> **Omegatron said:**
> What did you change about that file?

The file was:

```

auto eth1
iface eth0 inet dhcp
auto eth0
```

I had to change it into:

```
iface lo inet loopback
auto lo
auto eth0
auto eth1
```

It was a known bug in launchpad. After an Upgrade, Feisty makes this nasty little joke. You can find the launchpad page here:

[https://bugs.launchpad.net/bugs/26419](https://bugs.launchpad.net/bugs/26419)

I don't remember how my file was before upgrading to Feisty but it surely changed my file. Before that it worked and it had an lo entri, I remember it, so it was altered.

---

### Post by Omegatron on 2007-05-16
> **darkmaster said:**
> The file was:

It was a known bug in launchpad. After an Upgrade, Feisty makes this nasty little joke.

Hmmm...  Well Feisty worked fine for me at first.  It wasn't until I force shut down my computer that I started having these problems.  I may have been installing something new at the time, though, and I can't remember, so maybe that would have caused it?  Maybe I can look in an apt log file somewhere and correlate the time with when I know it happened?

If I enable Desktop Effects, it starts with the Compiz window manager on the regular session, and if I then turn off Desktop Effects it reverts to normal metacity.  But if I then log out and back in, metacity does not start again.

Again, the failsafe session seems to work fine.

---

### Post by darkmaster on 2007-05-16
> **Omegatron said:**
> Hmmm...  Well Feisty worked fine for me at first.  It wasn't until I force shut down my computer that I started having these problems.  I may have been installing something new at the time, though, and I can't remember, so maybe that would have caused it?  Maybe I can look in an apt log file somewhere and correlate the time with when I know it happened?

If I enable Desktop Effects, it starts with the Compiz window manager on the regular session, and if I then turn off Desktop Effects it reverts to normal metacity.  But if I then log out and back in, metacity does not start again.

Again, the failsafe session seems to work fine.

Weird... my problem appeared the very first time I upgraded to Feisty. I then used edgy for one more month, then upgraded again to see if things changed (I had a backuped version of edgy) but nothing changed and I decided to make it work somehow.

As for your problem, I suggest you to mention it in Launchpad, it helped me.

---

### Post by Omegatron on 2007-05-16
> **darkmaster said:**
> As for your problem, I suggest you to mention it in Launchpad, it helped me.

Yeah, I did.  Lots of suggestions but nothing that helps.  

[https://answers.launchpad.net/ubuntu/+question/6529](https://answers.launchpad.net/ubuntu/+question/6529)

---

### Post by darkmaster on 2007-05-16
> **Omegatron said:**
> Yeah, I did.  Lots of suggestions but nothing that helps.  

[https://answers.launchpad.net/ubuntu/+question/6529](https://answers.launchpad.net/ubuntu/+question/6529)

Did you try deleting all the configuration files I mentioned in one of the previous posts in this thread? After I did it at least the window decorator started loading fine...

---

### Post by Omegatron on 2007-05-16
> **darkmaster said:**
> Did you try deleting all the configuration files I mentioned in one of the previous posts in this thread? After I did it at least the window decorator started loading fine...

No, but I will try them later.

---

### Post by fermo111 on 2007-05-17
Same problem here with Feisty installed with 2 different computers.
The problem might have started after having done a 
```
sudo killall gnome-panel
```
or after having logged from remote with VNC.

I have tried to create a new account. Same problem. Therefore it is not something related to user conf files. I have checked /etc/network/interfaces and it is ok.

Finally I solved the problem in one computer uninstalling the ubuntu-desktop and reinstalling it. But I tried the same thing in the other computer and this did not work. Actually in the first case I removed other packages too but I don't remember which.

I am still struggling with this problem so any help is very welcome.

Luca

---

### Post by Omegatron on 2007-05-17
hmm

```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

---

### Post by Omegatron on 2007-05-18
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/106350](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/106350) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Bug 106350 seems to have fixed my problem.

---


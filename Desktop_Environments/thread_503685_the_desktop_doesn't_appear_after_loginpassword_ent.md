---
title: "the desktop doesn't appear after login/password entered , but..."
date: 2007-07-18
forum: Desktop Environments
---

### Post by yehudaco on 2007-07-18
i need help pls first i had a problem with the panels they've gone after i did something with some dock repositories in the synaptic but i managed to bring them back only i couldn't fix the trash can into them so i uninstalled all the gnome panel repositories and reinstalled them'only not exactly the same ones, i guess...
so now, when i restart the computer, after i log in - name and password, it get stuck on the brown screen but doesnt go any further, with the funny noise of getting into the sys and everything, it just stays there... i can do alt+ctrl+backspace or ctrl+alt +f2
please help me have my ubuntu back!!! thanks
p.s - i'm just a beginner so pls, if u can explain thoughtfully....

---

### Post by phidia on 2007-07-18
After you changed your repositories did you then do an update and/or install packages? Which version of ubuntu are you using? 

It probably makes sense to put your sources.list pack to the orgianlly installed state. You can do that by copying the /etc/apt/sources.list from a live cd to your system. Once that is done you can update and then re-install gnome. You also didn't specify which package manager your using, but from commandline you would do > sudo apt-get update  and then > sudo apt-get install gnome-common
Also see the [man pages]("http://linux.die.net/man/8/apt-get")

---

### Post by yehudaco on 2007-07-18
but my problem is that i can't do sudo apt-get update or sudo apt-get install gnome-common because i cant go into the garphical system and from the command line, in the stage before i see the desktop,i'm not connected then i use ctrl+alt +f2, it wouldn't be able to connect to the net and get the repos.  am i right?? how do i do that?? i'm using ubuntu 7.04 pls help me solve this...

---

### Post by phidia on 2007-07-18
Your system isn't connected in commandline? What type of internet connection do you have?
If you have a dial up you can use pon (isp name or default-depending how you set up your connection) to connect. If you have broadband please specify your connection then someone can help with that.

---

### Post by RandyNemo on 2007-07-25
Same problem after doing a update in 7.10.  after login in I don't get any desktop just the brown screen...Any thoughts

---

### Post by ibeardslee on 2007-12-20
I'm getting a similar problem after upgrading from fiesty.

When I login I just get the brown desktop, no background, no icons.  Toolbars at the top and bottom are there though.

If I start up a terminal and 'killall nautilus' and then run 'nautilus' it all comes back well.

Although I do also notice that sometimes that clicking on the door (at the top right) to exit it can take up to five minutes to actually bring up the shutdown/logout dialog box.  At this time I am assuming that the two are related.

Still digging.

---

### Post by ibeardslee on 2007-12-20
Sorted ... I think.  I found a post that mentioned that gnome settings getting slightly toasted during the upgrade.

I logged out of gnome and logged directly into the console (Crtl+Alt+F1) and renamed (mv)  ~/.gnome  ~/.gnome2 and ~/.gnome2_private

Logged back in again and all seemed to be fine.  Rhythmbox lost it's 'database' and a couple of the icons on the panel had to be replaced (evolution and rdesktop).

---

### Post by frost_ireland on 2008-02-21
> **ibeardslee said:**
> Sorted ... I think.  I found a post that mentioned that gnome settings getting slightly toasted during the upgrade.


Could you post the link of that post?  I've just started getting this problem, although I dont think it's related to an upgrade, last I did was more than a month ago.  However I've just put an SBS2003 server on the network and am now accessing internet through the server, when before I was going direct.  That's the only change I can think of that I did.

My exact symptom is similar, in that when I log in I can run applications but my desktop colour is the default and icons aren't there.
Killall nautilus' and then rerunning nautilus fixes it

---


---
title: "Is it safe to install Gnome 3 on Ubuntu 11.04?"
date: 2011-07-20
forum: Desktop Environments
---

### Post by goyle on 2011-07-20
I am eager to try Gnome Shell 3, but i have seen articles online which say that the PPA is unsafe.

So if anybody knows of a safe way to install Gnome 3 for 11.04, then please reply.

Thank you.

---

### Post by LordDelta on 2011-07-20
Not entirely.

I would say it is "unsafe", but not "impossible".

I accidentally installed it (I was messing around with a script that was claiming to install gnome3 "easily", never run untrusted scripts or ones you don't understand, good rule of thumb, thought it failed, and found out later it didn't), took me a while to figure out how to fix things back (get back to a reasonably themed desktop environment).

However, after I got my theming issues sorted (knowing a bit of css, that themes are in /usr/share/themes/ , that gnome-tweak-tool is the best graphical theme manager available for gnome3, and that gtk2 themes need to be updated to have gtk3 folders), I find it to be rather decent. Only thing is I have to use the "ubuntu" desktop otherwise I find this horrible painting bug, and I have to Ctrl+Alt+T every time and run nohup gnome-panel & to get my panel, because I'm too find out where the startup script is. :P

(Also, I'm still not entirely sure what that script was I installed, it might actually have been something I installed from a rep, if you need me to track it down, but it might have something to do with some of the major re-configuration changes I noticed)

Bottom-line is, proceed at your own risk. Conversely, I like it better, because my mouse is more stable (I was having issues with it...euh...not dragging things correctly), and it seems that the cpu usage is lower too.

Good luck!

---

### Post by Frogs Hair on 2011-07-20
Do some searching , when 11.04 was first released installing Gnome 3 would make impossible to restore Gnome 2.xx . I think there is a PPA purge now , but it does not work for everyone . What ever you decide , back up anything important .

---

### Post by mrinsult2000 on 2011-07-20
I have personally had a lot of bad luck installing it, three times now.  I will just wait for awhile until I try again.  

After I installed it everytime, the themes were all jacked up, but most importantly the fonts were all blurry, hard to read, etc.  I just reloaded after that, instead of trying to remove.

---

### Post by goyle on 2011-07-20
Thanks for all of your replies, after reading what you've all said I think i'll wait  a little longer, hopefully a safe and easy method will become available in time.

---

### Post by MARP1961 on 2011-07-20
I installed via the ppa route (which installs Gnome 3 and rids you of Unity) on Natty and have had no problems. It has been consistently stable and a vast improvement on the Unity Shell. If you want to try it quickly just get yourself a live Fedora 15 disk.

---

### Post by LordDelta on 2011-07-21
> **MARP1961 said:**
> I installed via the ppa route (which installs Gnome 3 and rids you of Unity) on Natty and have had no problems. It has been consistently stable and a vast improvement on the Unity Shell. If you want to try it quickly just get yourself a live Fedora 15 disk.

Would you mind screenshotting your experience? Which ppa? (there are several gnome3 ppas, I have gnome-session and the gtk3 libraries, for instance, but I don't have gnome3-session, which gnome-session "replaces", nor do I have gnome).

Basically I have gnome3 with a mix of gnome2/3 settings and apps. (e.g. gnome 2 gnome-panel). I'm looking for something closer to the old gnome2 experience, but that's gnome3. I don't want their "cleaner" gnome-shell desktop though, per-say. Mine was/is cleaner than theirs was (IMHO).

---

### Post by mswift on 2011-07-21
You do realize you can simply log into the
ubuntu classic desktop, which is Gnome2 desktop with the two panels?

---

### Post by Arbayong on 2011-07-23
Well, actually, i've had no problem installing gnome3 on my system (natty narwhal) on Toshiba l455d AMD version). I have gnome3, gnome classic (2.xxxx), unity3d (default for ubuntu 11.04) and unity2d sessions all working fine on the same systems. only problem is when install ATI catalyst control centre gnome3 tears my screen. i've removed ATI CCC and all's well no change in video or any other graphics performance.

This is my second time of mixing gnome3, gnome2, Unity3d, unity2d. first time i had xfce, and kde in addition to the above sessions. A partial and incomplete update messed up my system and i repaired the installation with unbuntu cd and reinstalled gnome3 with no problem.

go try gnome3. its coooooooooooo.

---

### Post by LordDelta on 2011-07-29
@mswift

Yes, I realize that. Or at least I used to be able to. One of things my gnome3 install did was remove those settings, I can't select between Ubuntu Classic/Unity any longer.

Doesn't matter, I used "Ubuntu" with the gnome desktop and no Unity ;)

@Arbayong

Nice to hear. Maybe someday my install will be that clean.

---

### Post by wjmac1973 on 2011-07-29
I would forgo Gnome3 , most times it messes up the new unity, I tried it and both were dog slow, switch back to classic Gnome interface or go to KDE - which is running fine on my Narwhal now. 
I sure hope ubuntu fixes this soon, its going to give them some press, I have never had a problem with their releases before , but for OS your only remembered for your latest release. 

These are the problems I had on unity - 
   poor performance, Banshee would not launch from launcher, 
Went to gnome 3 .. 
   in gnome3 performace was very slow, Banshee launch issues, firefox crashes 

Went to KDE - performance issues gone, Banshee working fine.

---

### Post by Arbayong on 2011-08-02
> **wjmac1973 said:**
> I would forgo Gnome3 , most times it messes up the new unity, I tried it and both were dog slow, switch back to classic Gnome interface or go to KDE - which is running fine on my Narwhal now. 
I sure hope ubuntu fixes this soon, its going to give them some press, I have never had a problem with their releases before , but for OS your only remembered for your latest release. 

These are the problems I had on unity - 
   poor performance, Banshee would not launch from launcher, 
Went to gnome 3 .. 
   in gnome3 performace was very slow, Banshee launch issues, firefox crashes 

Went to KDE - performance issues gone, Banshee working fine.

@WJMAC1973: I agree with you that kde desktop is cool on ubuntu natty narwhal. i tried. Perhaps the best desktop environment!! with lots of tweakability as well.

Gnome3 are both cool too but are trully slow. when i plug a broadband modem into the laptop under gnome classic desktop, the modem is recognised within 30secs and i can use it immediately. no so with unity and gnome3.... i have to have to issue the modprobe option command as root and wait for at least for minutes!!!!

Let's see how oneiric ocelot turns out.

note: gnome3, gnome classic and unity (+- kde, xfce) can all coexist peacefully. am talking from experience in using ubuntu 11.04

---

### Post by Arbayong on 2011-08-02
> **LordDelta said:**
> @mswift

Yes, I realize that. Or at least I used to be able to. One of things my gnome3 install did was remove those settings, I can't select between Ubuntu Classic/Unity any longer.

Doesn't matter, I used "Ubuntu" with the gnome desktop and no Unity ;)

@Arbayong

Nice to hear. Maybe someday my install will be that clean.
@ LordDelta. try to reinstall unity from synaptic package manager or terminal. it should resolve ur problem. it worked for me. gnome3, gnome classic, unity 3D and unity 2d all coexiting peacefully.

---


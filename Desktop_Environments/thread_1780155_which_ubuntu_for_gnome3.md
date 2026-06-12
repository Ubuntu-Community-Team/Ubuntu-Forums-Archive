---
title: "which ubuntu for gnome3?"
date: 2011-06-11
forum: Desktop Environments
---

### Post by snoopy-2009 on 2011-06-11
pretty sure this has not been asked. google didnt find an answer for me anywhere..

once i discovered ubuntu was capible of dual booting with windows, i never turned back... now im actually 100% linux, havnt touched a windows system (of my own) in over a year :P

imo, unity sucks... built for a netbook.. i actually had it on my netbook before 11.04 was out

but regardless, i STILL gave it the time after 11.04, got more adapt to it, and am (or was..) completely comfortable with it, til i saw gnome 3 ;)

im in love with the new gnome, and imo, if ubuntu wanted to break us in to the next generation desktop env. i say they should have gone with gnome! especially when it was going to be released the same month as natty..

anyway, enough of my rambling..


im attempting to get a stable gnome3 experience.. 

i have it on my desktop pc, on natty.. its pretty iffy   --a lot of issues going on there
i loaded it there first more of a try-out, to see if i liked it or not
which i did.. so now im trying to make sure i get a stable build on my hp dv7 laptop.

i downgraded natty to 10.04 LTS, thinking that would be a better option for gnome-shell..
its working great, but a few things im unsure about...

first of all, its a COMPLETELY DIFFERENT gnome3 desktop than the one ive seen the screenshots for (and the one on my desktop pc..lol)   instead of the iconic favorites sidebar, and the "scrollable" vertical (rightside) workspace switcher, i have this..
[IMG]http://www.3-60.co/public_share/Screenshot-4.png


which is OKAAAY.. but i really like the other one better... but im unsure how or why theres a difference..


really what im trying to ask, is which ubuntu is "preferred" or reccomended for gnome3? 

one thing ive noticed, is that when adding the ppa for gnome3-team in software sources, the apt-get updates dont work due to a 404 error not finding the LUCID version for gnome3... so back in software sources, i hit edit on the PPA, and changed it to Maverick, did the reload, and updates/upgrades, and this is what i got.

is that safe? it worked... seems stable.. is there a way to test something, other than just attmpting my usual tasks?

also, would it be safe to run the Natty gnome3 PPA on 10.04?
(thinking thats probably the version difference im seeing here..)

---

### Post by snoopy-2009 on 2011-06-11
jeez.. im sorry.. was there something else i was supposed to do to that img? just cliked the img button in the editor... i assumed it would be auto-shrunk.. or thumbnailed or such... i could have done it myself..

---

### Post by VOT Productions on 2011-06-11
The normal Ubuntu will be much better.
If you run into problems, [http://ubuntuforums.org/showthread.php?t=1742343](http://ubuntuforums.org/showthread.php?t=1742343) will help you.
Although it works on Fedora or OpenSUSE best.

---

### Post by gdonwallace on 2011-06-11
Essentially the Ubuntu variants are all the same, with just a different Desktop Environment.  (i.e. Lubuntu is Ubuntu with the LXFC Desktop, and ubuntu underneath.)  Some of the programs that are loaded are specific to the desktop, so some things will be different.  (i.e. Kubuntu uses the KDE desktop and all programs associated with KDE) 

Gnome3 is available for download from the Gnome website, and with the next version that is coming out, Unity will still be the "default" desktop, but Gnome3 will be in the repos for download.

---

### Post by snoopy-2009 on 2011-06-11
:mad:...****.. just lost my whole reply.... well...here goes attempt number two... 

> **VOT Productions said:**
> The normal Ubuntu will be much better..

what do u mean by "normal" ubuntu? i take it youre referring to natty?

i just ran into issues on my desktop pc installing that way, but i may get it right this time.

plus its all over google when u search for installing gnome3 on 11.04  not to do it, and its unstable, and breaks unity, etc etc..  but  breaking unity is fine by me, so its actually stable to do so if you  dont want unity?

> **gdonwallace said:**
>  but Gnome3 will be in the repos for download.

Very good to know! Thank you!



[B]so i guess the only questions i have left..

[/B]am i correct on the reason why the DE from the snapshot was installed on my system instead of the "official" one?  is the one i have the result of editing the PPA in my software sources from Lucid (gets a 404 error) to Maverick?   

Is there really no PPA for lucid?  is it SAFE to install the maverick gnome ppa on lucid? 
(..it seems stable to me--just not the version id prefer) 

and is it safe using this method to switch it to natty and install that ppa on 10.04?

---

### Post by Joe of loath on 2011-06-11
The Gnome 3 version on lucid looks interesting. It's not like it's a bug, because it's all fully formed, but it's not G3. Maybe it's one of the testing releases?

I'd mess about with the sources.list, worst case scenario is it refuses to install because of dependency problems.

---

### Post by snoopy-2009 on 2011-06-12
confirmed, thank you for your help. 

i believe any issues i had was due to my hdd beginning to fail (relocated sectors getting upto the thousands over just a few days)  

anyway, replaced the 500gb with an 80gb for now (ouch..lol) 

-fresh install of 11.04, 
-i told natty to install updates during OS installation (which i never seem to do, too time consuming, i usually run it all after)
-ran in terminal (for backup purposes): 
     sudo dpkg --get-selections | tee ~/.Conf.BAKs/default.natty.dpkg.list
-(copied in the backup of my old home folder)
-booted up, 
-i ran update manager, then directly after, followed the instructions from:
           [http://ubuntuforums.org/showthread.php?t=1742305](http://ubuntuforums.org/showthread.php?t=1742305)
 (which are:)

> **zzzz401 said:**
> in terminal type these commands 

sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install gnome-shell


-BEFORE reboot, i also ran (also further down on the same thread, fixes the graphical glitch):

> **slooksterpsv said:**
> sudo apt-get remove gnome-accessibility-themes
sudo apt-get install gnome-themes-standard


THEN did my reboot, and sure enough, gnome is then listed in the dropdown list on the login screen,
and its FREAKIN BEAUTIFUL!!

honestly, the window theme looks phenomenal!! better than the screenshots i had seen before!

now im gonna have to repeat the process on my desktop, n hope the graphical glitch error fix works next time... this is amazing :)

thanks for your replies and all, i may not have gone back to natty if i hadnt posted this and got the answers i did, im glad i made (what seems to be so far) the right choice! ive seen not a single error yet! (and im already multitasking.. lol, almost forgot to finish this and send it....!! :P )

 i hope this post ends up helping someone else as well! :) im very satisfied, and I LOVE G3! best Desktop Enviornment yet! (and WTG ubuntu for adding it in the reops for next release! Kudos!! )

---

### Post by Copper Bezel on 2011-06-13
> The Gnome 3 version on lucid looks interesting. It's not like it's a bug, because it's all fully formed, but it's not G3. Maybe it's one of the testing releases?
It looks like the October snapshot that was released, yes. The PPA snoopy used to install Gnome 3 on Ubuntu 10.04 probably hadn't been updated since then.

---

### Post by h313 on 2011-06-13
> **snoopy-2009 said:**
> 


THEN did my reboot, and sure enough, gnome is then listed in the dropdown list on the login screen,
and its FREAKIN BEAUTIFUL!!

:p Nice to heat that :p

Done the same procedure, worked out the graphics glitches too, and they are working for ubuntu and gnome classic. But :( i am not able to run G3 from gnome in the list. It says "something went wrong".
I think its an issue for my graphics card ATI hd 5470.
Please help me out.
When i choose gnome classic, gnome2.3 DE loads up
For the ubuntu option in the list, a partial unity and a partial gnome 3 environment comes up, which has unity launchers and gnome theme with a very few applications.

---

### Post by Joe of loath on 2011-06-13
Do you have the proprietary drivers installed for your video card?

---

### Post by mswift on 2011-06-13
What is your output of:

```
glxinfo | grep render
```

---

### Post by h313 on 2011-06-13
> **Joe of loath said:**
> Do you have the proprietary drivers installed for your video card?


i have ati/amd proprietary FGLRX graphics drivers installed

---

### Post by h313 on 2011-06-13
> **mswift said:**
> what is your output of:

```
glxinfo | grep render
```


> 

output :

spock@himanshu-inspiron-n5010:~$ glxinfo | grep render
direct rendering: Yes
opengl renderer string: Ati mobility radeon hd 5000 series
    gl_nv_conditional_render, gl_nv_copy_depth_to_color, 



Is this ok ?

---

### Post by mswift on 2011-06-13
You can try out the gallium driver for your video card.
(Uninstalling fglrx should do the trick)

---

### Post by h313 on 2011-06-13
> **mswift said:**
> You can try out the gallium driver for your video card.
(Uninstalling fglrx should do the trick)

i will try out gallium in a while and let you know.

Apart from this, when i checked into System Setting > System Info > Graphis.
It shows graphics drivers as " Vesa : Park ".
Any idea on what this means?

---

### Post by mswift on 2011-06-13
I'm sorry, no idea what's that supposed to mean.

---

### Post by h313 on 2011-06-13
It worked!!!
uninstalling the fglrx drivers, made gnome3 boot up with no pain.
Although, it is taking more time to boot up.
- which graphics drivers should i use now ? I guess reinstalling the fglrx drivers will bring up the same problem again.
- How should i improve the system performance now ?

---

### Post by mswift on 2011-06-13
Sorry, you will simply have to wait until
fglrx properly supports gnome-shell.
This could be this month, next month or next decade.
You never know with ati/amd.
Very impatient people can try the x-org-edgers-ppa,
however, be advised, that really can break your system.

---

### Post by h313 on 2011-06-13
if thats the case, then ill prefer being on the back seat and wait for a legitimate support.
Thanks for your help.

---

### Post by snoopy-2009 on 2012-01-23
yeah as far as i know we're still waiting haha..  as i just mentioned closing up  a similar post-- i dont need anything i dont have without the fglrx drivers..   but no, as far as i know, there arnt any other options for gnome-shell and ati   (at least not cards needing the fglrx drivers)  - - the only thing that didnt work last time i checked it was my hdmi plug.

---


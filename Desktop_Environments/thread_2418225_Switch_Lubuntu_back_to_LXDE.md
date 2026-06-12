---
title: "Switch Lubuntu back to LXDE?"
date: 2019-05-03
forum: Desktop Environments
---

### Post by notinkeys on 2019-05-03
Folks, I've tried. Really, I've tried to like LXQt. It has a few features I like, but fact is, I just don't like how it looks. Outside of reverting to an older version, is there a way to change my desktop back to LXDE? I'm not asking for a change in the direction of Lubuntu- I am just looking for a way to change my install. I've had a number of problems with LXQt and simply wish to move on. If I can't do it reasonably easily, I'm okay with that (there's always Xubuntu for those lightweight versions.)

---

### Post by mikewhatever on 2019-05-03
I don't know which release you have, so it depends. If it is 18.10 and newer, then no.

---

### Post by cruzer001 on 2019-05-03
I use to start my lubuntu build with just lxde.  It was a nice and bootable starting point.  But then I discovered on my rigs that Budgie was just as fast as Lue right out of the box.

I see the lxde package still exist.

[https://packages.ubuntu.com/eoan/lxde](https://packages.ubuntu.com/eoan/lxde)

---

### Post by notinkeys on 2019-05-03
> **cruzer001 said:**
> I use to start my lubuntu build with just lxde.  It was a nice and bootable starting point.  But then I discovered on my rigs that Budgie was just as fast as Lue right out of the box.

I see the lxde package still exist.

[https://packages.ubuntu.com/eoan/lxde](https://packages.ubuntu.com/eoan/lxde)

That's good to know. I'll also have to look at Budgie. Right now, I am going to install 18.04 on the old device I want to re-install. It's an old, but still useful, netbook. Not a lot of horsepower, but it serves the uses quite nicely. Small, light, non-reflective screen. Perfect for the beach. ;)

---

### Post by notinkeys on 2019-05-03
> **mikewhatever said:**
> I don't know which release you have, so it depends. If it is 18.10 and newer, then no.

I sed to change the desktop I used on occasion in older versions of Linux. Sadly, it doesn't look like that is very easy to do now...

---

### Post by notinkeys on 2019-05-03
> **cruzer001 said:**
> I use to start my lubuntu build with just lxde.  It was a nice and bootable starting point.  But then I discovered on my rigs that Budgie was just as fast as Lue right out of the box.

I see the lxde package still exist.

[https://packages.ubuntu.com/eoan/lxde](https://packages.ubuntu.com/eoan/lxde)

Cruzer, you freaking ROCK! That got me out of LXQt and I can now use LXDE on 19.04! It was as simple as apt install lxde!!!

---

### Post by cruzer001 on 2019-05-03
It went smoothly for you, excellent :)

don't forget

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by notinkeys on 2019-05-06
Gratefully done, sir.

---

### Post by cruzer001 on 2019-05-06
Just FYI

I have a 13 year old laptop with a single core processor and 2gig of ram that is running Budgie.  I do keep the install fairly vanilla, but with gnome3 a new world of bells and whistles await you (which are better known as extensions).  I still recommend you take it for a test drive one day.
):P

---

### Post by roler2 on 2019-05-19
I think LXQT is very confusing to configure and I am sad to see the probable end of life for LXDE. I was going to try Sparky Linux, but I don't think you are able to add the Ubuntu Repositories.

---

### Post by Rex Bouwense on 2019-05-19
You are only seeing the demise of lxde in Lubuntu.  It still exists in some 40 other distributions and for the time being is still in the Ubuntu repositories.
Sparky is based upon Debian testing.

---

### Post by DuckHook on 2019-05-19
LXDE *as an officially supported flavour* will go away, but I doubt that LXDE as a DE will. The repos host all sorts of unofficial DEs that one can install, from Enlightenment to Cinnamon. I suspect that LXDE will be around for a long time&#8212;just not as an "official" flavour.

See the link in my sig: The Best 'buntu Flavour.

---

### Post by roler2 on 2019-05-19
I am cursed! I tried to install LXLE and SparkyLinux. Both crashed at exactly 22%. Utilizing a USB, both booted to a live session just fine. After that. . .no luck and I liked SparkyLinux. I will have to get used to LXQT, it is just. . .right now. . .very frustrating because I am so used to LXDE. I just like the simplicity of LXDE. In terms of other LXDE Distros, many of them appear to be depleted, or not currently updated. LXLE and Sparky are the only two I have found that have recent OS updates. I didn't really understand why both booted to a live session just fine and then crashed at the same 22% when attempting an install when both Lubuntu 19.04 and Peppermint installed just fine.

---

### Post by DuckHook on 2019-05-19
Did you read through the link in my sig? It shows how to install LXDE from a command line environment. You can thereafter add only the apps you want, and won't get a leaner build than that.

---

### Post by cruzer001 on 2019-05-20
> **DuckHook said:**
> Did you read through the link in my sig? It shows how to install LXDE from a command line environment. You can thereafter add only the apps you want, and won't get a leaner build than that.
^^^ +1
Thats what is nice about Linux.  If you can't find what you want, then you can build your system to taste.  No one need be stuck with something they do not like.

---

### Post by roler2 on 2019-05-20
@DuckHook Yes I did read your link. Nicely done! However SparkyLinux already has LXDE but I could not install it as it crashed at 22%, so did LXLE. Peppermint OS is also based upon Lubuntu but looks a lot like LXQT, and so did LXLE. I would prefer SparkyLinux but could not install it. Let's say I install Lubuntu 19.04 or Peppermint and want the LXDE desktop. Which do I install from the command line? LXDE, lubuntu-desktop or lxde-core? And how do I uninstall LXQT or the Peppermint desktop, which does not look anything like the lubuntu desktop yet it is based upon Lubuntu?

---

### Post by DuckHook on 2019-05-20
The idea would ***not*** be to install Lubuntu or Peppermint, because they already come with a DE which will pollute your eventual environment. Instead, install the server version of Ubuntu which is command line only. No DE. Bare bones. Uber geek. But you won't be leaving it there. Afterwards, from command line:```
sudo apt install lxde
```It's as simple and as easy as that.

What this will do is install a very lean and simple LXDE environment—no Lubuntu, no Peppermint, no SparkyLinux. From there, you can use apt to install whatever additional packages you want. The result is a customized desktop environment based on LXDE with no vestige of Qt or anything else that you don't like.

---

### Post by roler2 on 2019-05-21
Thank you again! I did install Ubuntu Server and LXDE. Unfortunately, I read that the Ubuntu Server kernel has to be updated manually, given it is still on an earlier version and apparently cannot be updated automatically. LXDE installed a lot of Debian extras, which I could not figure out how to uninstall, and actually, was also kinda confusing to configure, especially the taskbar, much more so than the Lubuntu Desktop. I think I will just have to get used to LXQT. I have Lubuntu currently installed on. . .well. . .for me. . .a really wonderful old P4 32-bit. I have another 64-bit, but it isn't as good as the 32-bit. So I was hoping to keep the 32-bit running past 2021, but I will obviously have to give that up too.

Given that LXDE might not be in the Ubuntu Repositories in 2020 when 20.04 is released, and certainly the Lubuntu Desktop will be LXQT-based, I will just have to get used to LXQT and give up my beloved 32-bit. Sad.

However, thank you again for your wonderful suggestion!

---

### Post by ajgreeny on 2019-05-21
I am not sure about the server kernel versions, nor your comment about manually updating, but I suggest you don't use the server version; use the [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) site to download a MinimalCD version using the same kernels as the standard desktop version, just without any GUI at all, then add LXDE and any other packages you want.

I have done this in the past but generally just use Xubuntu.

---

### Post by cruzer001 on 2019-05-21
The server iso will do the same thing as the mini.iso, but takes a few more steps to install.  The kernel is the same and it will auto update.

At the beginning of the server install you need to hit the F4 key and choose basic install and later in the process you will be asked to choose what kind of server you wish to install, you then choose "none" (or however it was termed).  That will give you a console (text) only install.  Thats using the Alternate Server ISO.  Not sure if this applies to the standard server iso, I do not use it.

The server.iso has wifi built in, the mini.iso does not and thats a big plus if you live in a wireless house.  Thats the only difference I am aware of when used for a mini install.  If using a cable hookup then stick with the mini.iso, its just easier to figure out.

---

### Post by DuckHook on 2019-05-21
The mini.iso is a very valid route. The reason I don't start off with recommending it first is that it is missing the ingredients for a UEFI install. Consequently, it will set up a MSDOS MBR by default and go back to using yesterday's technology. If a user is happy with this, then the mini.iso is the better choice because it is simpler. However, if the user wants a UEFI-compliant system, either because of dual booting with Windows or just for future-proofing, then I recommend the server install.

Someone wrote instructions on how to modify a Xenial mini.iso to allow UEFI install, but I've lost the link :sad:

I've also read that the techniques used for that modification don't work for the Bionic mini.iso. Just hearsay, so I can't vouch for this info. If someone in-the-know could fill us in, it would be very useful.

---

### Post by cruzer001 on 2019-05-21
> **DuckHook said:**
> The mini.iso is a very valid route. The reason I don't start off with recommending it first is that it is missing the ingredients for a UEFI install.
Right you are, I forgot about UEFI 8-[

---

### Post by roler2 on 2019-05-21
Well. . .I did both the Server install and the mini.iso install. Unfortunately the Server install is 64-bit only. The mini.iso I could download in 32-bit. It appears to be, and I am by far no expert. . .geez I can't even configure a LXQT Task Bar, that either one will suffice. . .depending on what you want for a Desktop. Given the mini.iso I could install on my beloved bit rot 32-bit Dell P4, and then it gave me the option to install my beloved Lubuntu/LXDE bit rot Desktop, I really only had one choice. What was nice about the Server install and the mini.iso is that they both automatically installed the Canonical Livepatch. So now, as I posted another thread: "Will Lubuntu 18.04 still be able to install security updates subsequent to EOL?" Lubuntu is three years until 2021, Ubuntu is five years until 2023. Given I installed the Ubuntu mini.iso coupled with the Lubuntu Desktop, will I receive security/application updates until 2021, or will it be 2023?

Just as an aside, installing with the mini.iso coupled with the Lubuntu/LXLE Desktop appeared to me to boot up very fast, certainly appeared faster that utilizing a Lubuntu ISO. And it is exactly the same Lubuntu 18.04 Desktop, Programs and all. Also the fonts and graphics appear to me to be more brighter, clearer and crisp than utilizing a Lubuntu ISO.

Thank you all for your help! I hope this will be good until 2023!

---

### Post by ajgreeny on 2019-05-22
> **DuckHook said:**
> The mini.iso is a very valid route. The reason I don't start off with recommending it first is that it is missing the ingredients for a UEFI install. Consequently, it will set up a MSDOS MBR by default and go back to using yesterday's technology. If a user is happy with this, then the mini.iso is the better choice because it is simpler. However, if the user wants a UEFI-compliant system, either because of dual booting with Windows or just for future-proofing, then I recommend the server install.

Someone wrote instructions on how to modify a Xenial mini.iso to allow UEFI install, but I've lost the link :sad:

I've also read that the techniques used for that modification don't work for the Bionic mini.iso. Just hearsay, so I can't vouch for this info. If someone in-the-know could fill us in, it would be very useful.
Thanks for that also DuckHook; I had also forgotten about the UEFI problem, and I admit I was not aware of the fact that a server .iso had wifi already set up; that could be a big plus for some users.

You live and learn something new every day!

---

### Post by DuckHook on 2019-05-23
> **DuckHook said:**
> …Someone wrote instructions on how to modify a Xenial mini.iso to allow UEFI install, but I've lost the link :sad:
Found it!
[https://www.onetransistor.eu/2015/12/install-ubuntu-minimal-cd-uefi-enabled.html](https://www.onetransistor.eu/2015/12/install-ubuntu-minimal-cd-uefi-enabled.html)

---

### Post by DuckHook on 2019-05-23
> **roler2 said:**
> …Given I installed the Ubuntu mini.iso coupled with the Lubuntu Desktop, will I receive security/application updates until 2021, or will it be 2023?…

2018 + 5 = 2023

FWIW, in some respects, a CLI server install followed by Lubuntu-desktop or LXDE is superior to a straight Lubuntu install in the following sense:

If you install Lubuntu from its ISO, it will be retired in 3 years (i.e. it's repos get archived and are no longer updated).

[CENTER]vs[/CENTER]

If you install Ubuntu server or mini, followed by LXDE/Lubuntu DE, then this is treated as a mainline install of which the DE is only another "app". Therefore, it will get 5 years support. Moreover, you can update it to the next LTS to start the whole 5-yr cycle again. So long as the devs feel that LXDE is worth supporting, it will also continue to show up on the repos. Therefore, this method can take you far beyond the end date of the strict Lubuntu flavour.

A loophole? Or a feature? Like beauty, I suppose it is in the eye of the beholder.

---

### Post by cruzer001 on 2019-05-23
> 
A loophole? Or a feature? Like beauty, I suppose it is in the eye of the beholder.
Amen to that

Mini.iso + LXDE
In my eyes, that should of been end of story.  Guess the OP needs to chime in with a update.

---

### Post by roler2 on 2019-05-25
Ok I shall give an update! I utilized the mini.iso from the netboot download as it appeared to be affiliated with 18.04.2 (02/09). Install went smoothly however make absolutely sure you are connected to Internet before even starting to install (lesson learned). Then when it gets to the section where you can choose what type of Desktop you prefer, I chose the Lubuntu Desktop but there were others there that you could install (Gnome, etc.). Quite handy. You could skip the section and choose another Desktop after install was finished and just install the Desktop you want via command line. The Lubuntu Desktop looks exactly like. . .well. . .the Lubuntu Desktop! That went smoothy too. I noticed I got a couple of gigs extra space via this method. As I mentioned earlier, the fonts appear, at least to my old eyes, clearer and crisper, and again to my old eyes, it boots faster, Internet is excellent, shut down is faster, Applications start up quicker, etc.

20.04 might be a problem, as the Repositories will be for 20.04 and that would install the LXQT Desktop. So, via the command line, I would probably have to delete the 20.04 'main' Repository (no code name yet), and add the 'Bionic' main Repository, and then attempt to install the bit rot 18.04 Lubuntu Desktop.

---

### Post by roler2 on 2019-05-25
In addition, from my understanding, if  one installs the bit rot 18.04 Lubuntu Desktop utilizing the 20.04 mini.iso, I think you can re-add the 20.04 'main' Repository and delete the 18.04 Bionic 'main' Repository, and then, when you run updates, 'hold' the automatic attempt to upgrade to the LXQT Desktop: sudo apt-mark hold lubuntu-desktop, or possibly: sudo apt-mark hold lubuntu desktop*.

---

### Post by roler2 on 2019-05-25
To be safe, via the command line, I believe one may also purge the other three 20.04 Ubuntu Repositories, replacing with the Bionic multiuniverse, universe and restricted, prior to install of the bit rot 18.04 Lubuntu Desktop. Then after install of said Desktop, I believe one can then access the actual sources.list, which will still show 'Bionic', and manually replace 'Bionic' with the code name for 20.04, for each distinct Ubuntu Repository.

---

### Post by roler2 on 2019-05-25
If you could please let me know if the below commands are correct to remove/add Ubuntu Repositories. Given the 18.04 Repositories will still be active until April, 2023, I believe I can keep those respective 18.04 Repositories in the sources.list after install of the Lubuntu LXDE Desktop, even though I will be utilizing the 20.04 mini.iso in April, 2021: 

sudo add-apt repository --remove main universe multi-universe restricted (I don't believe a code name is needed)
sudo add-apt repository bionic main universe multi-universe restricted
sudo apt update
sudo apt install lubuntu-desktop

Then after install:

sudo apt-mark hold lubuntu-desktop
sudo apt-mark hold lubuntu-desktop*
sudo add-apt repository [20.04 code name needed] main universe multi-universe restricted
sudo apt update


Thank you for your valued assistance.



[FONT=arial, sans-serif][SIZE=2][COLOR=#6a6a6a][/COLOR][/SIZE][/FONT]

---

### Post by cruzer001 on 2019-05-25
Hello roler2
Your welcome, glad to assist.  But..

Sorry, this is wrong.  20.04 does not exist yet and there is no need to change your repositories and no need to add the lubuntu desktop to your install.

Here are the steps:
#1 Install the mini.iso. Do not add any packages or desktops to this, leave it as a text only install.  Next:
#2 Add the lxde desktop to the install
```
sudo apt install lxde
```
#3 Update this install
```
sudo apt update
```
#4 Upgrade your install
```
sudo apt full-upgrade
```
and reboot
```
reboot
```
You now have a pure lxde desktop

For good measure follow this with a cleanup
```
sudo apt autoclean && sudo apt autoremove
```
Please feel free to ask any questions, thats what were here for :)

---

### Post by roler2 on 2019-05-25
Quoted from one of my prior posts within this particular topic:

[COLOR=#000000]". . .I utilized the mini.iso from the netboot download as it appeared to be affiliated with 18.04.2 (02/09). . .when it gets to the section where you can choose what type of Desktop you prefer, I chose the Lubuntu Desktop but there were others there that you could install (Gnome, etc.). . .[/COLOR][COLOR=#000000]20.04 might be a problem, as the Repositories will be for 20.04 and that would install the [/COLOR][COLOR=#417394]LXQT[/COLOR][COLOR=#000000] Desktop. So, via the command line, I would probably have to delete the 20.04 'main' Repository (no code name yet), and add the 'Bionic' main Repository, and then attempt to install the bit rot 18.04 Lubuntu Desktop. . ."


My question applicable to the 20.04 Repositories is a 'future' question applicable to when 20.04 is released in April 2021, and installing the Lubuntu LXDE Desktop package rather than the Lubuntu LXQT Desktop package. My question was not affiliated with installing the distinct LXDE package.

I have already installed the Ubuntu 18.04 mini.iso and installed the Lubuntu LXDE Desktop package and, overall, it appears to me to be working even better and more efficient than installing from the Lubuntu ISO. You can utilize either the 18.04 Ubuntu Server version, only available in 64-bit, or the 18.04 mini.iso, 32-bit or 64-bit. The Ubuntu Server install is strictly command line and updates the kernel automatically. The mini.iso install has more of a graphical interface and does not update the kernel automatically. With the Server you have to install the Desktop enviroment via command line, the mini.iso allows you to choose the respective Desktop environment.[/COLOR]

---

### Post by cruzer001 on 2019-05-25
Have you not noticed the title of this thread?  You have gone off thread.  Better to start your own thread with a proper title and request, a lot less confusing that way.  Perhaps a mod will come along and clean this up.

---

### Post by QIII on 2019-05-25
This hijacked and now derailed thread is closed.

@notinkeys:  If your original issue was not addressed, please feel free to start a new thread.

---


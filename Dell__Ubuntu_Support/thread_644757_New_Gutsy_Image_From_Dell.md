---
title: "New Gutsy Image From Dell"
date: 2007-12-19
forum: Dell  Ubuntu Support
---

### Post by notwen on 2007-12-19
I was curious if anyone has had an opportunity to install the new Gutsy image from the [Dell Linux Wiki]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10").  I have a 1420n and it seems like we get all the possible issues,although it  looks like most have workarounds.  I was curious about other user's experience after installing this new Dell Gutsy image?      I was hoping to install Gutsy on my 1420n before new years.  Please share your experiences, issues and/or thoughts. =]

---

### Post by clove on 2007-12-19
I just installed the new Gutsy image on my 1420n but I was disappointed to find that the install process didn't offer any partitioning options or means of setting up whole-disk encryption (important to me on a laptop), so now I'm right back to the standard Gutsy 'alt' install disc.

Also, I couldn't get Compiz to work at all with the new image (if you're interested in that).

---

### Post by RobertGloverJr on 2007-12-19
I have a Dell 1420n that came with Feisty pre-installed.
   Last month when the laptop first arrived I tried to install Gutsy and it broke everything, so I used the option to restore to the factory settings, which put Feisty back on.
   I have no idea what the new Gutsy ISO from Dell will do, for that matter what will happen if I plop it into the DVD reader-- I have no experience with this. I don't want to burn any bridges, but I sure would like to have Gutsy working.
   Will it remove my ability to restore back to the factory settings, i.e., Feisty.
    Anecdotes/war stories much appreciated.

---

### Post by natehall on 2007-12-19
Seems like everybody was trying to download this . It was stalled for so long I gave up. I figured I would wait a little bir longer until traffic died down.

---

### Post by fragos on 2007-12-19
I got my Dell 7.10 last night.  You can install live CD style but I chose the factory upgrade which only provide a one distribution install.  Everything I've used works well.

---

### Post by natehall on 2007-12-20
> **fragos said:**
> I got my Dell 7.10 last night.  You can install live CD style but I chose the factory upgrade which only provide a one distribution install.  Everything I've used works well.

Did'nt you have the 1420N with Fiesty preinstalled? I have the DVD all ready to go but I'm not sure where to go from there.

---

### Post by fragos on 2007-12-20
> **natehall said:**
> Did'nt you have the 1420N with Fiesty preinstalled? I have the DVD all ready to go but I'm not sure where to go from there.

I did have 7.04 pre-installed but use 7.10 on my Desktop and use a video editor that required libraries with 7.10 to run.  I'm also one of those nuts that upgrade Ubuntu every release.  I just love all the latest application versions.

---

### Post by notwen on 2007-12-20
> **fragos said:**
> I did have 7.04 pre-installed but use 7.10 on my Desktop and use a video editor that required libraries with 7.10 to run.  I'm also one of those nuts that upgrade Ubuntu every release.  I just love all the latest application versions.

Tempting, I'll have to download the new image and once I have enough time to back everything up I'll give the new image a try.  Thanks for the info. =]

---

### Post by drkm_4_frm on 2007-12-20
I did a fresh install of gusty with dell's new image on my 1420n and every things is working fine as it did with fiesty. 
The only thing is i'm not able to get compiz-fusion working!

---

### Post by fragos on 2007-12-20
Apparently the video driver for the Intel chip don't support some features Compiz uses.  Compiz has blacklisted this chip but some claim a work around to al least get it to work somewhat.  After thinking about I decided I didn't want the shorter battery life that might result from the use of processing power for the eye candy.  FYI: the nine cell battery I ordered with my 1420n gives over 5.5 hours.

---

### Post by RobertGloverJr on 2007-12-20
The  Dell OS Reinstallation 7.10 DVD ISO is over 4 gigabytes.  It takes a long time to download.  I'd like to buy a DVD containing it and have it mailed to me.  Anybody know of a place that'll sell it?

---

### Post by fragos on 2007-12-20
Sounds like a good idea.  Why don't you post the request on Direct2Dell.

---

### Post by yron87 on 2007-12-21
Have you tried calling Dell for support? I dunno if here in Malaysia they have it... hmmm let me check :)

---

### Post by meateater on 2007-12-21
Any idea if the 1420 ubuntu image will work with the 1520?

---

### Post by jdelaros1 on 2007-12-21
The Dell DVD iso is a Live DVD, much like the one you can download from ubuntu.com, You can boot to it in a live environment and browse around it, without wiping out your hard drive. If you wish to use it to install Gutsy (and wipe out your hard drive), be sure to read the instructions at [http://linux.dell.com/wiki/index.php/Ubuntu_7.10/OS_Reinstallation#Reinstalling_from_DVD_disc](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/OS_Reinstallation#Reinstalling_from_DVD_disc).

Be sure to download the correct image (Intel or nVidia video) as each iso contains workarounds/fixes for each card. As for Compiz on Intel video, this feature has been blacklisted in Gutsy because of video playback issues, but there's a way to override it:

[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility)

Yes, the iso is huge, so I would suggest start the download in the evening and let it run overnight. It's highly unlilkely that Dell will sell or ship the iso, as it is provided as-is, no support of any kind.

---

### Post by anjilslaire on 2007-12-21
I bought a 1420 wih Vista for the nvidia 8400m, & also got the intel wireless, zero'd the drive & installed the standard kubuntu 7.10 iso from canonical. Everything works fine. Restricted drivers installed, even Hibernate. I'm impressed.

---

### Post by RobertGloverJr on 2007-12-21
Can anyone advise a newbie (me) where the best place to download the Dell gutsy ISO to is
.  
    Would a good place be my home directory in it's own directory?  

    After I wait hours and hours for the 4gig download to complete, can anyone explain to me and the other newbies what the best way is to burn it to a DVD?   I have a DVD writer on my 1420n but have never burned a DVD before in Ubuntu.  Is there a special command or utility to use?

   Also, is it true that booting/installing  from the DVD will completely trash everything on the hard drive?  How does one go about making a backup before hand?  Are people backing up to a DVD?  Are they using some special sort of software to do the backup?

    What if there is a disk error on the DVD.... I will then be totally hosed with a brick on my hands?  Is there a way to verify the DVD before booting from it?

    I have feisty installed on the 1420n-- it came from Dell that way when I bought it on November 17.

---

### Post by fragos on 2007-12-21
Your home folder is OK.  I do all downloads to my Desktop so I can work with them directly.  To write a DVD: right click the ISO and select "Write to Disc...".

---

### Post by natehall on 2007-12-21
What if there is a disk error on the DVD.... I will then be totally hosed with a brick on my hands?  Is there a way to verify the DVD before booting from it?


You can do a live DVD boot. See if it works and then if you are pleased   
 just do the Install. ( I just did , so far so good) I backed up everything on memory sticks myself and even saved my bookmarks on hotmail. (I do all my e-mail web-based so I can easily ignore spam without having to download it.)  Be sure and write down any passwords you might need for websites, Its easy to get lazy and let Firefox remember it for you then wipe it all out for a fresh install)

---

### Post by natehall on 2007-12-21
Thanks for that link, it had just what I was looking for!

---


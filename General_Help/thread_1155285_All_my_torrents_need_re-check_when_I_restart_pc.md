---
title: "All my torrents need re-check when I restart pc"
date: 2009-05-10
forum: General Help
---

### Post by ovisan on 2009-05-10
Hello,
I  very new to linux, just installed Ubuntu                           [9.04 ]("http://ubuntuforums.org/showthread.php?t=1129123&highlight=torrent") y-day. I use torrents a lot but seems that linux is not  very torrent friendly. By default I was using transmission, I downloaded a few torrents everything as nice and dandy until I had to restart my PC. When I ve logged in again all my torrents were gone and i had to re-download and re-check each one again. I ve checked these forums and you said that Vuze its a good clinet. I ve deleted Transmission and installed Vuze the default version (3 . something) I ve tried to update it to the latest version with no luck. I was getting some strange errors and everything went back to the old version. I am not the only ne with this problem, there are others and the mystery is still unsolved. I ve installed Deluge and ktorrent and again the torrents just vanish from my clients.  I ve closed my clients every time i ve logged off. i m running ktorrent now... seems allrite
Do I have to download all the torrent in the same folder?
answer to [pastalavista]("http://ubuntuforums.org/member.php?u=521710"): i ve just downloaded the torrent file and then re-checked not the whole thing again
There is probably a simple answer to my problem but I am so noob I just cant figure it out myself. All I want is someone to tell me how to keep my torrents is the client even after I log off and log on again

Cheers

---

### Post by AndThenWhat on 2009-05-10
I am not an expert on the subject of Transmission, but it sounds like maybe transmission is not able to write its settings to disk.  Check and make sure that the folder /home/[your_user_name]/.config/transmission/ is there and has the proper file permissions for Transmission to write to it.

By the way, the ".config" folder is hidden so if you are looking for it in your home folder, you have to press CTRL+H to see it.

---

### Post by pastalavista on 2009-05-10
One thing you need to realize is Linux is nothing like Windows. You certainly shouldn't have had to redownload the torrent files. Do you know where you saved them? You didn't say why you "had to restart" or how. It's easy to make mistakes when you don't know what you're doing. In the future it would be better if you asked BEFORE you go and make a lot of changes. That's all I have to say except transmission is a great application and I've never had any trouble with it. Your problem is somewhere else.

---

### Post by lovinglinux on 2009-05-10
I think AndThenWhat is right. It is probably a file permission issue. I remember a similar thread posted not a long time ago, but I can't find it. As far as I remember, the problem was solved after fixing the permissions settings.

BTW, I personally recommend using Deluge. It is the number one client in my opinion. Transmission is too simple. Vuze is bloated and uses Java, which tends to put an extra load on your CPU.

EDIT: you might also check if you have configured the client to move completed downloads to another folder.

---

### Post by ovisan on 2009-05-11
Cheers for yre answers chaps. I still dont dont know how to fix it. I m gonna read a few  guides, understand how linux works and then post again.  laters

---

### Post by AndThenWhat on 2009-05-11
If you need help learning how Ubuntu works this is a really helpful guide:

[http://ubuntuguide.org/wiki/Ubuntu:Jaunty](http://ubuntuguide.org/wiki/Ubuntu:Jaunty)

---

### Post by gradysghost on 2009-05-11
I agree with lovinglinux.  Deluge is a fantastic program that I found after finding Transmission to be a bit simplified.  I also didn't care much for the whole individual windows for each torrent thing.  But check your file permissions.  That's a good start.

---

### Post by ovisan on 2009-05-11
> **gradysghost said:**
>   But check your file permissions.  That's a good start.

Could you please tell me HOW to do it mate...

---

### Post by pastalavista on 2009-05-11
I've found the easiest way to change permissions (without the command line which I've messed things up with more than fixing them) is to open a root browser ```
gksu nautilus
``` Then just navigate to the file/folder you need to change and Right-click->Properties->Permissions.

---

### Post by ovisan on 2009-05-12
That didnt helped mate...Do you recon reinstalling will sort it?  dont kno what to do

---

### Post by lovinglinux on 2009-05-12
Try this:

[http://ubuntuforums.org/showthread.php?t=1030841](http://ubuntuforums.org/showthread.php?t=1030841)

---

### Post by ovisan on 2009-05-12
I ve reinstalled umbutu and i still having the same problemo. The torrents need rechecking  after restarting my PC and I have to set manually the destination folder to re-check(when I turn my client on it says: No suck file or destination).
I got a similar problem with Rhythmbox: I drop all my music in it, I can listen to the tracks but when I restart my PC all the tracks go to the missing file directory...
I ve also got this when i try to update. Am I too thick for this OS? I ve read a couple og guides but I still find it hard to use...


Cheers

---

### Post by ovisan on 2009-05-13
i m really gutted about this lads... if anyone else can give a piece of advice is welcomed... Another thing please explain clearly cause I m  a nob head when it comes to linux... I i m really gutted about this lads... if anyone else can give a piece of advice is welcomed... Another thing please explain clearly cause I m  a nob head when it comes to linux... I like it, I want a change but it simply aint having it. I dont even kno where linux is installed on my pc....

I ve tried
Code:

gksu nautilus

But I ge an error message:

Failed to run nautilus as user root.

Unable to copy the user's Xauthorization file.

---

### Post by michy99 on 2009-05-13
This is just a guess, but I have a feeling that you are saving your files to a partition that is not automatically mounted when you boot. If that is the case, your torrent program, music player or whatever can not see them until you mount the partition. If you open the folder in Places or Nautilus, it mounts the partition for you,, so you probably don't even realize this is happening. Try this: Reboot the computer. Before opening anything else, open the folder with your files in Nautilus. Now if your torrent program starts without problem that is what is happening. If so, it is pretty easy to fix it so it will mount at start-up.

---

### Post by ovisan on 2009-05-13
> **michy99 said:**
> This is just a guess, but I have a feeling that you are saving your files to a partition that is not automatically mounted when you boot. If that is the case, your torrent program, music player or whatever can not see them until you mount the partition. If you open the folder in Places or Nautilus, it mounts the partition for you,, so you probably don't even realize this is happening. Try this: Reboot the computer. Before opening anything else, open the folder with your files in Nautilus. Now if your torrent program starts without problem that is what is happening. If so, it is pretty easy to fix it so it will mount at start-up.


You are a star! Cheers

Is there any way I can set automount on my HDs?

---


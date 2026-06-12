---
title: "Help a n00b out please!"
date: 2005-02-22
forum: Desktop Environments
---

### Post by Pitbull11188 on 2005-02-22
I just installed Ubuntu(Warty) on my computer and I think I may be running as the root user. This is because under the Users and Groups function I don't see any username that says anything like root, all I see is the usernames that I have added after the install and the one it prompts you to add upon install. Please help. 

*I'm sorry I just read the before you post, after i posted, but I don't know how to move my topic. My apologies to the moderator.*

---

### Post by hashimoto on 2005-02-22
The root account in Warty is disabled by default. The first user you added has root privileges (using "sudo").

See [http://www.ubuntulinux.org/support/documentation/faq/root/](http://www.ubuntulinux.org/support/documentation/faq/root/)

---

### Post by Pitbull11188 on 2005-02-22
Thankyou Hashimoto that explained everything! Also, a question on Gnome, How do I resize or ??? my desktop because about 1/2 an inch on the right side is cut off. I can only see 1/2 of my trashcan and 1/2 the A in AM next to the time. Thanks.

---

### Post by rmjokers on 2005-02-22
If the resolution and refresh rate are set properly, then you might need to adjust the settings on your monitor to get it to display properly.  There is no way to adjust these settings from windows/linux as far as I know.  Or, you could try a different refresh rate as this sometimes has an impact on the position/size of the picture displayed on the monitor.  See Computer->System Configuration->Screen Resolution

---

### Post by hashimoto on 2005-02-22
Actually, there is a piece of software to help position the screen, but I just can't remember the namo. I'll come back later.

---

### Post by kassetra on 2005-02-22
[QUOTE=Pitbull11188]Thankyou Hashimoto that explained everything! Also, a question on Gnome, How do I resize or ??? my desktop because about 1/2 an inch on the right side is cut off. I can only see 1/2 of my trashcan and 1/2 the A in AM next to the time. Thanks.[/QUOTE]

You need to adjust your monitor by using the monitor's controls (similar to the ones that allow you to set brightness & contrast)

---

### Post by hashimoto on 2005-02-22
The name is xvidtune. Note my sig.

---

### Post by Pitbull11188 on 2005-02-22
Thankyou for helping me with the problem. All I had to do was hit the autoadjust button on my moniter, and it centered the screen for me.

---

### Post by kassetra on 2005-02-22
[QUOTE=Pitbull11188]Thankyou for helping me with the problem. All I had to do was hit the autoadjust button on my moniter, and it centered the screen for me.[/QUOTE]

Awesome!  :)  I wish I had that function on my monitor!  :)  (I have to use a funky "menu" that I go through to adjust horizontal and vertical size/position)

---

### Post by Pitbull11188 on 2005-02-22
Ok I know that I'm being a pain asking all these questions, but how do I unprotect files that I copied from a CD I made of all my documents, pictures, movies, and songs? 
I'm also not sure how to uninstall programs.
Thanks.

---

### Post by kassetra on 2005-02-22
[QUOTE=Pitbull11188]Ok I know that I'm being a pain asking all these questions, but how do I unprotect files that I copied from a CD I made of all my documents, pictures, movies, and songs? Thanks.[/QUOTE]

1. You're not being a pain.
2. As in, you burned a cd with all your stuff, and now when you want to copy your stuff to your new ubuntu home directory, it has locks on it? -- if that is the case:
3. You'll need to know your username & group... I'm pretty sure you know your username, but to get your group type this in a terminal:
 ```
ls -l /home/username/Desktop
``` 
(the group is in the third column, or the column just to the right of your username)
4. Now, to fix your files that you copied from the cdrom, let's say you put the directory "pictures" from the cdrom into your /home/username, here is how you would change the directory & all of the files in it:
 ```
chown -R username:group /home/username/pictures
chmod -R 775 /home/username/pictures
``` 

Does that make sense?

---

### Post by Pitbull11188 on 2005-02-22
That makes perfect sense, however the terminal line which you specified didn't work. I got a reply which said:

[CENTER]"ls: /home/username/Desktop: No such file or directory"[/CENTER]  

     Also, I got this information from Computer->System Configuration->Users and Groups, however I'm not sure hoe to enter the last two lines of code. I keep getting this reply:

[CENTER] chown -R username:group /home/username/pictures
chown: failed to get attributes of `/home/username/emoticons': No such file or directory[/CENTER] 

Thanks, never mind I got it to work. I forgot to change the second username under the home directory.

---

### Post by kassetra on 2005-02-22
[QUOTE=Pitbull11188]That makes perfect sense, however the terminal line which you specified didn't work. I got a reply which said:

[center]"ls: /home/username/Desktop: No such file or directory"[/center]
  

 Also, I got this information from Computer->System Configuration->Users and Groups, however I'm not sure hoe to enter the last two lines of code. I keep getting this reply:

[center] chown -R username:group /home/username/pictures
chown: failed to get attributes of `/home/username/emoticons': No such file or directory[/center]
 

Thanks, never mind I got it to work. I forgot to change the second username under the home directory.[/QUOTE]

I'm glad you got it to work, although not having a Desktop directory is kind of odd..  I would have thought that a "Desktop" directory was a standard ubuntu install...  Otherwise, where does it store items you place on your desktop...  hmmm must ponder this.

---

### Post by Pitbull11188 on 2005-02-22
It is standard install, however I didn't want icons so i directed my files into my /home/user file instead of my /home/user/desktop file. Sorry about the confusion. Also, could you please tell me how to uninstall a file that i downloaded and tried to install, but which only installed half way. Its a Skype file if that helps. Thanks.

---

### Post by kassetra on 2005-02-22
[QUOTE=Pitbull11188]It is standard install, however I didn't want icons so i directed my files into my /home/user file instead of my /home/user/desktop file. Sorry about the confusion. Also, could you please tell me how to uninstall a file that i downloaded and tried to install, but which only installed half way. Its a Skype file if that helps. Thanks.[/QUOTE]

apt-get purge Skype

or 

Open Synaptic and have it deal with the broken file for you.  :)

Ubuntu doesn't install icons on your desktop in the standard install... but it still should have created the directory... unless you removed the directory?

---

### Post by Pitbull11188 on 2005-02-22
Thanks I thought I had to do that from a terminal. Also, the folder is still there I just don't save to it. Also, how do I configure sound? Thanks.

---

### Post by kassetra on 2005-02-22
[QUOTE=Pitbull11188]Thanks I thought I had to do that from a terminal. Also, the folder is still there I just don't save to it. Also, how do I configure sound? Thanks.[/QUOTE]

Nope, synaptic can handle everything except when you download a file from somemwhere and want to install it from your local computer.

Ok, when you say how do you configure sound, what do you mean?  Does your volume not work?  Can you not play cds?  mp3s?

---

### Post by Pitbull11188 on 2005-02-22
My volume is stuck on zero and I get a prompt saying:


[CENTER]"sorry no mixer or sound device found"[/CENTER] 


     I can't play any sound! Also, my speakers are hooked in correctly because I used them just fine with WinXP before switching. Thanks.

p.s. I hate to pile on the problems but I'm having trouble installing firestarter. The terminal keeps saying that the packet was not found.

---

### Post by kassetra on 2005-02-22
[QUOTE=Pitbull11188]My volume is stuck on zero and I get a prompt saying:
"sorry no mixer or sound device found".[/QUOTE]

Assuming you have gstreamer-0.8 installed, type this in the terminal:
 ```
gst-register-0.8
```

And you should have sound... if not, let me know.

---

### Post by Pitbull11188 on 2005-02-22
I don't have gstreamer installed and i can't apt-get it for some reason it says: 

"E: Couldn't find package gststreamer0.8-mad"


     Also, the name that you gave me for it didn't work either. About the firestarter question in my last post, I think i may be putting in the wrong name in apt-get i input  
"sudo apt-get install firestarter", but it doesn't find it. This is exactly what happens with gstreamer.Thanks.

---

### Post by Buffalo Soldier on 2005-02-22
That error message most probably mean you did not add the universe repository in Synaptic. At the Synaptic toolbar, go to Settings -> Repositories -> check (enable) the universe section(s).

Then search for **gststreamer0.8-plugins** , it will install all available plugins for gstreamer.

---

### Post by kassetra on 2005-02-22
[QUOTE=Buffalo Soldier]That error message most probably mean you did not add the universe repository in Synaptic. At the Synaptic toolbar, go to Settings -> Repositories -> check (enable) the universe section(s).

Then search for **gststreamer0.8-plugins** , it will install all available plugins for gstreamer.[/QUOTE]

Yep, this is exactly what you need to do, also the "universe" sections will allow your firestarter to install as well.

then you can do the command I told you to enable your sound.  :)  (it might even work as soon as you install the extra files!)

---

### Post by Pitbull11188 on 2005-02-22
Ok, I got firestarter but for some reason get a message that states that i put in the wrong root password which I know I didn't. Also, I'm still having problems with gstreamer. Could some one please show me what lines of code to enter into the terminal.Thanks.

---

### Post by Buffalo Soldier on 2005-02-22
What are the problems you're having with Gstreamer?

---

### Post by Pitbull11188 on 2005-02-22
I can't get it to install.

---

### Post by kassetra on 2005-02-22
[QUOTE=Pitbull11188]I can't get it to install.[/QUOTE]

gstreamer is installed by default in ubuntu, but I assume you can't get it upgraded to the 0.8 version?

---

### Post by Pitbull11188 on 2005-02-22
Yes thats what I mean, sorry about the confusion. Also, if you have aim/gaim/trillian please im me at pitbull11188.

---

### Post by kassetra on 2005-02-22
Do this:
Close synaptic if it's open

 ```
sudo gedit /etc/apt/sources.list
``` 
and put in these lines at the end:

     deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
     deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
     
     deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted
     deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted
     
     deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse
     deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse

save the file, close it, re-open synaptic and click reload.
now install gstreamer0.8-plugins

---

### Post by Buffalo Soldier on 2005-02-22
Or what you can do is update the source.list file as said by Kassetra, and then at the terminal type:```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install gstreamer0.8-plugins
```

Other related threads on UbuntuForums about Gstreamer:

[thread=13285]Rhythmbox 0.8.8[/thread]

[thread=16526]How can i play Streamtuner streams with Rhythmbox?[/thread]

[thread=12928]MP3 problems[/thread]

---

### Post by Pitbull11188 on 2005-02-22
Ok I fixed firestarter by creating a root user "sudo passwd root". I working on gstreamer now.

---

### Post by Buffalo Soldier on 2005-02-22
Would you mind showing your /etc/apt/sources.list content?

---

### Post by Pitbull11188 on 2005-02-22
I will if you tell me how to, also the sound problem is persisting I have the apps installed however there is still no sound. Audio channels is blank so I think i may need to configure hardware or something.

---

### Post by Buffalo Soldier on 2005-02-22
Open a terminal and type **gedit /etc/apt/sources.list** and then copy&paste whatever gedit diplay in here.

---

### Post by Pitbull11188 on 2005-02-22
Here you go:


deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted 


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe  
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe  

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 
 deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse

Thanks for all the help you guys have given me I need to get to bed but hopefully i'll be able to resolve the sound issue soon.

---

### Post by Buffalo Soldier on 2005-02-22
All of the repositories are in your source.list file. Everything looks fine. Was there any error message when you typed **sudo apt-get install gstreamer0.8-plugins** in the terminal?

---

### Post by gmc on 2005-02-22
[QUOTE=hashimoto]The name is xvidtune. Note my sig.[/QUOTE]

Yes, xvidtune will allow you to adjust adjust monitor settings but it also gives you enough rope to hang yourself too. Unless you know what you're doing with it, it is possibe to damage your monitor or video card with it. Since the original poster is a noobie and I'm guessing relatively new to Linux/Ubuntu. I'm not sure recommending this tool is such a good idea.

---

### Post by Pitbull11188 on 2005-02-23
No it didn't give me any error messages it just installed perfectly, so i don't have any idea what is wrong with it. Also, I have an epson 1000 ics printer and i cannot get it to work, neither can i get my floppy drive to work. This is very important to me because I am a soph in hs and need to write and print papers very often. Also, I'm not sure how to make a data cd. If anyone knows how to fix these problems specifically the printer and floppy drive it would be greatly appreciated. If I can't solve them I will have to go back to windows and so far I like linux MUCH better. Thanks.

---

### Post by Pitbull11188 on 2005-02-23
Also I checked and my sound is supported it is: 

 Creative Labs
	

Sound Blaster Live!
	

emu10k1
	

The only thing is mine reads "emu10k1X"

---

### Post by Buffalo Soldier on 2005-02-23
[QUOTE=Pitbull11188]No it didn't give me any error messages it just installed perfectly, so i don't have any idea what is wrong with it.[/QUOTE]
[list=1]
[*] Then it seems you have all the gstreamer plugins :)

[*] Now, what happens when you try using Rhythmbox? (Applications -> Multimedia -> Music Player)

[*] About your soundcard. Try typing **lsmod** at the terminal and  do you see a **snd_EMU10k1** in the list?
[/list]

---

### Post by Pitbull11188 on 2005-02-23
1. Awesome

2. It opens normally but i can't play the radio

3. No I don't see it all I see is:

Module                  Size  Used by
isofs                  33976  0
udf                    79876  0
proc_intf               3968  0
freq_table              4356  0
cpufreq_userspace       5336  0
cpufreq_powersave       2048  0
ipt_ttl                 2176  1
ipt_limit               2688  34
ipt_state               2304  7
iptable_mangle          3072  0
ipt_LOG                 6272  1
ipt_MASQUERADE          3968  0
ipt_TOS                 2688  0
ipt_REDIRECT            2432  0
iptable_nat            22828  2 ipt_MASQUERADE,ipt_REDIRECT
ipt_REJECT              6656  1
ip_conntrack_irc       71604  0
ip_conntrack_ftp       72244  0
ip_conntrack           32640  6 ipt_state,ipt_MASQUERADE,ipt_REDIRECT,iptable_na t,ip_conntrack_irc,ip_conntrack_ftp
iptable_filter          3072  1
ip_tables              16896  11 ipt_ttl,ipt_limit,ipt_state,iptable_mangle,ipt_ LOG,ipt_MASQUERADE,ipt_TOS,ipt_REDIRECT,iptable_nat,ipt_REJECT,iptable_filter
button                  6936  0
ac                      5132  0
battery                 9740  0
ipv6                  230148  8
af_packet              20872  2
8139too                23936  0
8139cp                 19072  0
mii                     4864  2 8139too,8139cp
crc32                   4608  2 8139too,8139cp
uhci_hcd               29328  0
usbcore               104292  3 uhci_hcd
hw_random               5652  0
pci_hotplug            30640  0
intel_agp              20512  1
agpgart                31784  1 intel_agp
rtc                    12216  0
pcspkr                  3816  0
floppy                 54996  0
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
parport_pc             32064  1
lp                     10436  0
parport                37320  2 parport_pc,lp
tsdev                   7168  0
evdev                   9216  0
ide_cd                 38276  0
cdrom                  35872  1 ide_cd
mousedev               10124  1
psmouse                17800  0
ext3                  109672  1
jbd                    54552  1 ext3
ide_generic             1664  0
piix                   12576  1
ide_disk               16768  3
ide_core              125272  4 ide_cd,ide_generic,piix,ide_disk
unix                   26160  684
fan                     4236  0
thermal                13200  0
processor              17712  1 thermal
font                    8576  0
vesafb                  6688  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb

Thanks for the help. Also, if you know anything about printers please help.

---

### Post by Buffalo Soldier on 2005-02-23
About the printers I hope someone with better knowledge in this can help you. Or maybe you can start a new thread with a better title soley for that printer problem. Such as "epson 1000 ics printer problem".

Now about you Rhythmbox, do you have problem in playing only radio? or sound files (such as .mp3, .ogg) as well?

Try typing **sudo gedit /etc/modules** at the terminal. Add **snd_EMU10k1** to the list.

Reboot and see if it works.

---

### Post by Pitbull11188 on 2005-02-24
I did as you said but it didn't work. I dont have any mp3's to play right now as i need to get my disk back from a friend. Also I don't know if its important but, the thing is mine reads "emu10k1X" not  snd_EMU10k1. Thanks.

---

### Post by mike998 on 2005-02-24
Might I suggest a little bedtime reading for you?
Try checking out the unofficial ubuntu guide at [http://ubuntuguide.org](http://ubuntuguide.org) ?  It will take you through some of the easy steps to get things installed on your system and is very useful - I have a copy of the website that I use for reference when I reinstall on my laptop.
Good Luck and enjoy!

Sorry, This is not related to your problems with sound.  This is more a general help for you.

---


---
title: "Let's have Fun with U: Newbie's Attack"
date: 2006-03-02
forum: Desktop Environments
---

### Post by Peacepunk on 2006-03-02
Hi. First post here.

Let's laugh a bit with the newbie's issues: UBUNTU on a Sony Vaio widescreen subnotebook.

1. Widescreen / Sure Forums are there for, so I found 955resolution should help. right? well, this is where it's fun:
- un-taring the barbaric-named stuff: OK
- Change de dir to the new one (set in tmp): cd tmp no such file of directory... :) Good, it's really starting great. I later happen to achieve switching to the 955resolution-0.5.2 folder, and theennnn....
-make
What make ? Console said "no such command". :p  

That's where you suppose to laugh.

One more for the road:
2- Ubuntu doesn't like WPA, and my WiFi box is WPA. Ok, I "downed" my security levels to WEP during first setup, using my PC to control the Box. All for the Love of Free Software. Putted in an s:****** as key, and went on.
Didn't work for sure, so I eventually completely dropped, disabled the security, using only MAC filters. Open the Network setup: You'll discover that "no" is not an option: You have WEP either ASCII or HEX, and your password is in. Connection works IF I erase the password... Well, OK, so far so... Damn, when you close the network settings, it locks the Net again. Re-open, found my Password is there again... You are now allowed to laugh again: When I change a setting from the setup-time one, it reverts back to original if you close the dialogue. :-D 

Workaround: fire the dialoge, change it, leave it open, surf.

and a last one:

Wanted/needed SKYPE. They have a .deb available for download, OK, now... Huh, "unsupported archive format" Oh, sure, it's a package, I should fire up something specific. I did. Only to discover that you can install listed packages, or CDRom ones, but not a simple piece of .deb hanging around your HD :mrgreen: 

You laugh if you want. What do you think? Out of the box, no network, no sound, no widescreen, no DVD playing, and not even able to install stuff... Well, about Skype, I would not have lost time & bandwith if I had noticed the sound issue.

And I am a newbie with a Xandros Desktop. Works great.

---

### Post by cronholio on 2006-03-02
> Only to discover that you can install listed packages, or CDRom ones, but not a simple piece of .deb hanging around your HD

sudo dpkg -i <filename>

---

### Post by cronholio on 2006-03-02
> cd tmp no such file of directory...

Tried "cd /tmp"?

> What make ? Console said "no such command".

You can install make through Synaptic.

---

### Post by towsonu2003 on 2006-03-02
[QUOTE=cronholio]
You can install make through Synaptic.[/QUOTE]
```

put cdrom in
make sure it is mounted
sudo apt-get update
sudo apt-get install linux-headers-`uname -r` build-essential checkinstall
```

now to compile stuff: 
make sure you have all the dependencies
cd /path/to/extracted/targz
./configure (may say "no configure", that's fine)
make
sudo checkinstall

PS. if you don't install checkinstall, replace sudo checkinstall with sudo make install

---

### Post by Peacepunk on 2006-03-03
Thanks for all this - Timezones makes me looks poorly reactive, but I will check and try the above suggestion (although I think the last one is looking a bit too much complicated). But, the good thing with command lines: You can alwys try, it's so resistive you won't probably get more than another error message...

I did try cd /tmp: remembers me other times... Where nobody was complaining about Dos 6.22: Internet did not exists back then !

sudo dpkg -i <filename> is probably first thing in the morning to me.

thanks from the newbie.

Xandros OEV & UBUNTU certainly have their respective flawnesses. Long Live the Free Software - Well, long enough so it finaly gets easy, so I can really make choices.

---

### Post by cronholio on 2006-03-03
> Long Live the Free Software - Well, long enough so it finaly gets easy, so I can really make choices.

You should definitely read this: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by firecat53 on 2006-03-03
Brave the command line! WPA is actually fairly easy to get running....plenty of posts on techniques.  At home, I can turn on or suspend my laptop and have WPA/internet up and running automatically with no interaction required!

Good luck...Scott

---

### Post by az on 2006-03-03
This is pretty useless, so let's see what we can do here.  If you are actually interested in posting here, perhaps you will help out.

[QUOTE=Peacepunk]Hi. First post here.

Let's laugh a bit with the newbie's issues: UBUNTU on a Sony Vaio widescreen subnotebook.

1. Widescreen / Sure Forums are there for, so I found 955resolution should help. right? well, this is where it's fun:[/QUOTE]

What howto?  Show us so that someone can fix it.  It is obviously missing steps.

[QUOTE=Peacepunk]
That's where you suppose to laugh.[/QUOTE]


At you?

[QUOTE=Peacepunk]
One more for the road:
2- Ubuntu doesn't like WPA, and my WiFi box is WPA. Ok, I "downed" my security levels to WEP during first setup, using my PC to control the Box. All for the Love of Free Software. Putted in an s:****** as key, and went on.
Didn't work for sure, so I eventually completely dropped, disabled the security, using only MAC filters. Open the Network setup: You'll discover that "no" is not an option: You have WEP either ASCII or HEX, and your password is in. Connection works IF I erase the password... Well, OK, so far so... Damn, when you close the network settings, it locks the Net again. Re-open, found my Password is there again... You are now allowed to laugh again: When I change a setting from the setup-time one, it reverts back to original if you close the dialogue. :-D 

Workaround: fire the dialoge, change it, leave it open, surf.[/QUOTE]

Have you installed wpasupplicant?  That's usually step one on any tutorial.

[QUOTE=Peacepunk]
and a last one:

Wanted/needed SKYPE. They have a .deb available for download, OK, now... Huh, "unsupported archive format" Oh, sure, it's a package, I should fire up something specific. I did. Only to discover that you can install listed packages, or CDRom ones, but not a simple piece of .deb hanging around your HD :mrgreen: 

You laugh if you want. What do you think? Out of the box, no network, no sound, no widescreen, no DVD playing, and not even able to install stuff... Well, about Skype, I would not have lost time & bandwith if I had noticed the sound issue.[/QUOTE]

Skype is proprietairy.  That's why it's not in the repos.  Until it's free-libre, I'll use the alternatives, thank you.  I don't really like the idea of installing things you get from websites.  You don't know what your getting.  It's like stepping in poo.

[QUOTE=Peacepunk]
And I am a newbie with a Xandros Desktop. Works great.[/QUOTE]

It's proprietary, too.  But if that's what makes you happy, more power to you.  I couldn't really care what you run on your box.

---

### Post by towsonu2003 on 2006-03-03
> **Peacepunk]
I did try cd /tmp[/quote]
is this to compile? if so, and *if* you extracted the source code into /tmp:
example: you are compiling qemu-0.8.0-<blabla>.tgz  said:**
> 
sudo dpkg -i <filename> is probably first thing in the morning to me.make sure you have dependencies of the to-be-installed package first
[QUOTE=Peacepunk]long enough so it finaly gets easy, so I can really make choices.[/QUOTE]
you'll get use to it ;) :PpP

---

### Post by kuys on 2006-03-03
[QUOTE=cronholio]You should definitely read this: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)[/QUOTE]

Great article I must say. 

It's true, comming from windows to a linux distro is like relearning dos all over again. I'm definatley humbled by it but excited about the prospect of actual customization of my working enviroment.

---

### Post by Peacepunk on 2006-03-04
I am very happy to find myself in accordance with the above mentionned article "linux is not windows". the Lego-Fanatic & Sidecar driver myself really agrees to this vision, thanks Crohnolio. Alternative and Control are the keywords here.

Thanks ThomsonU for the Tech advice. I just re-installed the full stuff this morning, so I am ready to tackle issues with Forum help (As a member of this community, I will post into the Newbie Area an Howto on fixing my WiFi problem. I know that's the way, and I found some solution **Done, check bottom of message**).

Now, yes, dear Azz, you were supposed to laugh at me. Kindly enough you post solutions I haven't looked for since - for a newbie I am.

[http://users.skynet.be/thomasvst/linux-on-laptop/](http://users.skynet.be/thomasvst/linux-on-laptop/)

is the full breed step-to-step for Widescreen, specific to Ubuntu. Issue is abundantly documented, my point here was the 'make' command, not to seek for an HowTo. I am happy to provide the community with an actual Howto that looks excellent.

And yes, scott, I'd be delighted to switch back to WPA 'constantly Renewed' protection. A little link, maybe ?

My Contrib to Wireless setup / Illiterate Dummies Way:
[http://www.ubuntuforums.org/showthread.php?p=790759#post790759](http://www.ubuntuforums.org/showthread.php?p=790759#post790759)

Hey, at least this was posted using Ubuntu! We are making progresses here...

---

### Post by Peacepunk on 2006-03-06
Update on Screen Status / Widescreen (as one of the issues on my Sony Vaio Subnotebook): Some GOOD NEWS here folks.

UBUNTU Users: be aware that 915resolution (as well as the previous 855resolution) are available through Synaptic. Use the search button, then click on install. You may have to enable "universe" servers in synaptic to access 915resolution

Follow then the below link:

[http://users.skynet.be/thomasvst/linux-on-laptop/](http://users.skynet.be/thomasvst/linux-on-laptop/)

to know what should be done after synaptic has installed 915 resolution for you. Sipmle command lines, really. I achieved it, so most probably you can.

Newbies' note: Recommand you print down the commands, as you have two to input on a blacked SixtiesComputing Taste of Screen.

I had a tougher time with the permanent, boot time hack, as the above tute doesn't give you the way to save and get out of the last command line before "Reboot & check"; That's mostly due to me, sure. I saved the target file rectified with proper screen resolution some place else (desktop) as depicted in the above tute using a simple "text editor" ( right-click on /etc/init.d/bootmisc.sh - open with >> Text Editor) , then used in a terminal:

sudo cp -f /home/desktop/bootmisc.sh /etc/init.d/bootmisc.sh

to replace the file unedited with the one containing the "starter" for 915resolution & your actual resolution (you sure do not have the right to edit /etc/init.d files, so you may have to change the properties for the folder init.d and the file bootmisc.sh. Not sure, because "sudo" is suppose to allow you things. Otherwise, check the End-of-Post Link to work out "chmod" command. really easy. You'll Chmod like a pro in no time.)

I found a useful newbies help in this archive (chmod, copy, all basic bash cmmands fro a termina)l:

[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

Most Bash commands contains hyperlink to detailed use of it + samples.

\\:D/

---


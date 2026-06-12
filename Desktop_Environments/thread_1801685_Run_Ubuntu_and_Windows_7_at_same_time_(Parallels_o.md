---
title: "Run Ubuntu and Windows 7 at same time (Parallels or . . . .?)"
date: 2011-07-10
forum: Desktop Environments
---

### Post by jjb2011 on 2011-07-10
I saw a Mac friend run Windows side by side by Mac using Parallels 6. It  ran smoothly and beautifully. No need to reboot like I have done to get  to a Windows program. Can also cut and paste from Ubuntu to Windows 7  and back (64 bit). Can Parallels (or anything else?) do this for us  Ubuntu users? It would be a killer app? I see Parallels has a Windows  and Linux version that stopped at version 4 (back in January 2009). Told  that those earlier versions weren't great on Mac. The version 6 is not  clear about whether it works with Linux -- seems to be Mac only.  (Virtualbox sounds like too much work). 

Thoughts?

---

### Post by An Sanct on 2011-07-11
Well, setting up Virtualbox and maintaining it is exactly like setting up and maintaining an actual computer, so if you are looking for 100% windows support (note, that it is not meant for gamers!), then that is the way to go.

The alternative to that is WINE.

---

### Post by haqking on 2011-07-11
> **jjb2011 said:**
> I saw a Mac friend run Windows side by side by Mac using Parallels 6. It  ran smoothly and beautifully. No need to reboot like I have done to get  to a Windows program. Can also cut and paste from Ubuntu to Windows 7  and back (64 bit). Can Parallels (or anything else?) do this for us  Ubuntu users? It would be a killer app? I see Parallels has a Windows  and Linux version that stopped at version 4 (back in January 2009). Told  that those earlier versions weren't great on Mac. The version 6 is not  clear about whether it works with Linux -- seems to be Mac only.  (Virtualbox sounds like too much work). 

Thoughts?

Virtual Box
Vmware

Most people prefer Virtual Box, I have about 30 Virtual machines, i can run  a Windows XP, Vista, BT5, Mac Osx altogether at the same time (though you wouldnt really want to ;-)

works fine with every operating system i know of.  I run x64 bit Linux as my host, and have a guest for just about everything from NT4 through to Windows 7, from Haiku to Mac OSx

---

### Post by An Sanct on 2011-07-11
Well, I agree here :), V-Box is great :)

PS.. I Googled up Parallels ... and its just a Virtual Machine, like VirtualBox ... just it costs 80$ (don't bother me about that cent ... here, I'll give it to you!)

---

### Post by An Sanct on 2011-07-11
Here is a small screenshot of Windows in "seamless" mode, along with Android (presenting Jet-boy, the game)...

PS. Seamless mode is something to make people stare ;) ... VirtualBox also has clipboard and file and folders sharing (to name two...)

---

### Post by jjb2011 on 2011-07-11
OK, I'll give it a try. I read about 10 reviews that said it wasn't easy to set up (not like Windows, Mac or Ubuntu - just click set up and follow the prompts). And it was 32-bit only but I suppose it is finally 64-bit? So I'll give it a try.

Do you run VBox within Ubuntu or within Windows? Does one have better performance than the other? And if within Windows, why not Wubi? 

I'm running Ubuntu 11.04 64bit. Any one have experience with VBox? I know we are all geeks but ideally I want to find solutions that I can make easy for real people who just "want it to work." Otherwise, things like Ubuntu will never get market share, wireless drivers, etc. (which I would really like to see!).

---

### Post by jjb2011 on 2011-07-11
Well, I have an educational discount and can get it for $30 (Parallels). Just heard from Parallels that version 6 is coming out for Linux.

Correct me if I'm wrong but I read (repeatedly) that Virtual Box will NOT let you copy and paste between OS's but Parallels will. That would make Parallels worth $30. 

But I download Vbox and will try tonight.

---

### Post by An Sanct on 2011-07-11
> **jjb2011 said:**
> Well, I have an educational discount and can get it for $30 (Parallels). Just heard from Parallels that version 6 is coming out for Linux.

Correct me if I'm wrong but I read (repeatedly) that Virtual Box will NOT let you copy and paste between OS's but Parallels will. That would make Parallels worth $30. 

But I download Vbox and will try tonight.

I'm not saying "do not spend 30$" for Parallels, if you consider it good, buy it.

Here is a small screenshot of the setting, you can manipulate about clipboard (see attachment), you can choose from bidirectional, one way (host->guest or guest->host) or disabled.

edit: PS. The version I am using is 64bit, supports and also neatly utilizes multiple processor cores, 2D / 3D acceleration (Windows only). Installation is from within the Software Center (an "one click" thing) and is "just as hard" to set up and maintain as if you would have another computer next to your main machine.

---

### Post by jjb2011 on 2011-07-11
Wow! This is great. I download a Windows and a Ubuntu file from elsewhere but if it is in the Software Center - GREAT!

---

### Post by wildmanne39 on 2011-07-11
Hi, I have been using it for several years now and I have no problems with virtualbox, I do install mine from virtualbox.org because that use to be the only way to get usb support, but I am not sure that is the case anymore.

Also it is a good idea to read the documentation at the virtualbox website before you try to install, it is a great guide for setting up virtualbox.

---

### Post by jjb2011 on 2011-07-11
OK, I already have Ubuntu 11.04 and Windows 7 dual booted (separately). All the videos I see show you how to install Virtualbox in Ubuntu AND THEN install Windows in that "space."

I stopped installation because I got the point where it says "create a boot disk partition" OR use an "existing partition." Well, I have Windows and Ubuntu on the computer already so what do I do? Put another Windows within Ubuntu? The problem is I have no more licenses and don't want to pay $100 for a redundant copy of Windows. 

Or do I put Ubuntu within Windows? I'd like Ubuntu to be my primary (where I keep documents, etc.) and eventually go over to Linux entirely in the future and use special Windows-only programs on my laptop. 

Advice? Thanks. And glad to hear Vbox works well once you get it up and running.

---

### Post by demarshall on 2011-07-12
> **An Sanct said:**
> I'm not saying "do not spend 30$" for Parallels, if you consider it good, buy it.

Here is a small screenshot of the setting, you can manipulate about clipboard (see attachment), you can choose from bidirectional, one way (host->guest or guest->host) or disabled.

edit: PS. The version I am using is 64bit, supports and also neatly utilizes multiple processor cores, 2D / 3D acceleration (Windows only). Installation is from within the Software Center (an "one click" thing) and is "just as hard" to set up and maintain as if you would have another computer next to your main machine.

Thanks An Sanct! I've been using Virtualbox for a while but wasn't aware that files and clipboard could be shared, how easy it was or where the settings were.  Is there any reason to not have the setting set to bi-directional?

---

### Post by wildmanne39 on 2011-07-12
> **jjb2011 said:**
> OK, I already have Ubuntu 11.04 and Windows 7 dual booted (separately). All the videos I see show you how to install Virtualbox in Ubuntu AND THEN install Windows in that "space."

I stopped installation because I got the point where it says "create a boot disk partition" OR use an "existing partition." Well, I have Windows and Ubuntu on the computer already so what do I do? Put another Windows within Ubuntu? The problem is I have no more licenses and don't want to pay $100 for a redundant copy of Windows. 

Or do I put Ubuntu within Windows? I'd like Ubuntu to be my primary (where I keep documents, etc.) and eventually go over to Linux entirely in the future and use special Windows-only programs on my laptop. 

Advice? Thanks. And glad to hear Vbox works well once you get it up and running.Hi, if you have a windows disk you should not have a problem installing windows in virtualbox, also if you go to virtualbox.org it will tell you what you need to know, I think I posted that you should go there and read the documentation before you install virtualbox or a vm.

When I create a new partition I choose dynamic and give it plenty of room to grow, see it is a virtual partition not a physical partition and you can set it to a  large number and it will only take up as much space as required for the install, then it will grow when you add more programs to windows. 

With virtualbox if you want to uninstall windows all you do is click on it and delete and it is gone because it is in side a virtual environment,please read the documentation at virtualbox.org it will save you a lot of time and trouble.

Also you can use the windows you have installed already and put that in virtualbox but it is not easy in my opinion and you are better of having it separate.

---

### Post by An Sanct on 2011-07-12
> **demarshall said:**
> Thanks An Sanct! I've been using Virtualbox for a while but wasn't aware that files and clipboard could be shared, how easy it was or where the settings were.  Is there any reason to not have the setting set to bi-directional?

I have really no idea :) You see, (me speaking as a developer) some developers see good functionality in ideas they implement, that most people would simply live without. So *I know not* why this was made ... it has **some** functionality :) :) :) maybe it was a security thing at java, to keep the source code from unix/linux/JVM hosts to flow towards windows guest (????) go figure :) or 'sudo make me a sandwich' :) who knows ... ;)

---

### Post by jjb2011 on 2011-07-12
Dear Wildman,

I'll re-read (am working two jobs now - while the work lasts!). Problem is I bought a five-license DVD of Windows 7 Ultimate but run out (the disc is only $10 with educational discount. 

Most people I know have Windows and add Ubuntu (that's what I did). Other people - the real "geeks" (no offense meant) -- built Ubuntu/Linux machines and then add Windows. Since there are precious few machines that come with only Linux (unless you build one), I wondered what is the most common way Vbox installs:

1. Windows into a Ubuntu-only machine? (That would be easy and the safest route). 

2. Ubuntu into a Windows machine? (Easy too). But if an infection takes down Windows, would it take down Ubuntu too? 

Or the state I'm in: 

3. Ubuntu in a Windows and Ubuntu machine (dual boot)?  This is where I get queasy because there seems there would be one Windows and one virtualized (Vbox) Windows. Any one have experience with that? 


I have an hour this afternoon and will read more on Vbox.org  Thanks again.

---

### Post by wildmanne39 on 2011-07-12
> **jjb2011 said:**
> Dear Wildman,

I'll re-read (am working two jobs now - while the work lasts!). Problem is I bought a five-license DVD of Windows 7 Ultimate but run out (the disc is only $10 with educational discount. 

Most people I know have Windows and add Ubuntu (that's what I did). Other people - the real "geeks" (no offense meant) -- built Ubuntu/Linux machines and then add Windows. Since there are precious few machines that come with only Linux (unless you build one), I wondered what is the most common way Vbox installs:

1. Windows into a Ubuntu-only machine? (That would be easy and the safest route). 

2. Ubuntu into a Windows machine? (Easy too). But if an infection takes down Windows, would it take down Ubuntu too? 

Or the state I'm in: 

3. Ubuntu in a Windows and Ubuntu machine (dual boot)?  This is where I get queasy because there seems there would be one Windows and one virtualized (Vbox) Windows. Any one have experience with that? 


I have an hour this afternoon and will read more on Vbox.org  Thanks again.Hi, 

1. I do not think there is a most common way to install virtualbox.

2. Yes if windows has a virus bad enough to cripple it then ubuntu would be crippled also.

3. I have windows installed in a dual boot, but I have not booted it since last November, but I keep it because for one, I paid for it, two because there are a couple of things that do not work well in virtualbox like playing window games, and sound can be a little choppy if I tried to watch netflex in virtualbox windows. 

Now I have never tried to get the sound fixed because instead of using my computer to watch movies I bought a Roku box so I can watch them one my tv. 

I almost never boot windows in Virtualbox either, I just do not have the need, but if you are that busy and if you are maybe in school giving your time concerns you should keep a dualboot system and there is nothing wrong with having virtualbox with windows on it in ubuntu.

4. As for the license issue you may have to put ubuntu in virtualbox on windows we a prevented by law of discussing that issue very much, so I am going to leave that up to you.

---

### Post by jjb2011 on 2011-07-12
[LEFT]I got the two programs (MS Office) and Procite (notetaking/bibliographic software) working via PlayonLinux. Ditto with my PDF program (PDF-XCHANGE Viewer). 

I get grief from Ubuntu people for using MS Office but my last book involved a lot of track changes with four editors around the country. I don't have the luxury of working around Open Office and it wouldn't work anyway. 

PlayOnLinux is great, BTW. 

The only stuff that doesn't work is a) high-end scanning software I rarely use; b) wireless adapters -- I have ONE that works on one of my computers Wireless is a big problem but I think I'll buy a Pangolin next time if they are still in business. They seem to be the only ones to make computers for Ubuntu. 

Thanks for sharing your experience. Ditto on Roku or streaming. 
[/LEFT]

---


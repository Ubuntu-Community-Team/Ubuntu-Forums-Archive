---
title: "Noob Wine user"
date: 2006-02-04
forum: Desktop Environments
---

### Post by Jiganto on 2006-02-04
So I installed the "winesetuptk" file using synaptic, found the executable file under /usr/bin, ran the setup, it seemed to have worked fine. Then what?

How exactly do I use wine? I've googled around a bit n tried searching this forum, but can't seem to find "how to" about using wine. How do I install and run software using wine? I also can't seem to find any other folders or files that were created with the setup program. Detailed help would be greatly appreciated.

I know I'm a noob.:confused:

---

### Post by ESPOiG on 2006-02-04
well if u have installed it right... for basic program u can just double clik and .exe or maybe right click and then select open with wine

or u can do 'wine /location/program.exe'
to eneter config u do 'winecfg'
to find version u do 'wine --version'

or u can goto their irc channel #winehq @ irc.freenode.net

and the wine emulation actual windows folder will be installed in /home/usr/.wine/drive_c

that is if i remember everyhting right

---

### Post by John Jason Jordan on 2006-02-05
[QUOTE=ESPOiG]well if u have installed it right... for basic program u can just double clik and .exe or maybe right click and then select open with wine[/QUOTE]
I'm in the same boat. Just installed Wine, totally a n00b, and have no idea how to use it.

I do understand right-clicking on an .exe and selecting open with Wine. Problem is, I have no .exe files. That's because no Windows programs have been installed. And that's because I have no clue how to install a Windows program in Wine. I know Windows programs do all kinds of eldritch things to the registry, they scatter files all over, and the setup utility will puke up all over your computer if the slightest thing is out of sorts.

So could someone take me back to the beginning? How do I install a Windows program in Wine?

---

### Post by Jiganto on 2006-02-05
see the thing is, there is no "wine" in /usr/home, that's what confuses me, because that's where it says it installs it. And if I run the setup program again it acts as if it's already installed and asks if I want to write over existing files. Also, I have a WarCraftIII CD just as a test, and I right click the .exe files in it to find "wine" to open it with, and there is not "wine" in the list.

---

### Post by ESPOiG on 2006-02-05
no the wine directory is (in ubuntu) '.wine' and in there there is a folder called 'drive_c' and that is basically the windows hdd that u wuld find if u were using windows

to installed programs use 'wine theapplication.exe' or right click it and select open with wine, it will then if it works correctly and is not a program that needs tweakin... will then open ur basic installtion wizard that u get wen installin programs in windows.... with this u can just install as per norm as u wuld in windows, and if everything works fine then u will have a icon/link/shortcut on ur desktop if the installer allowed one and u shuld be able to run the program

to unistall the program you have to goto the directory u installed it in so ~./.wine/drive_c/program files/theapp/unistall.exe or wateva it is quite simple as long as it is a basic program with not much tweakin and messing around with

unlike ultima online... fark that is hard to get running :P

---

### Post by John Jason Jordan on 2006-02-05
[QUOTE=ESPOiG]no the wine directory is (in ubuntu) '.wine' and in there there is a folder called 'drive_c' and that is basically the windows hdd that u wuld find if u were using windows ...[/QUOTE]
OK, I have 64-bit Breezy with chroot and Wine is installed in chroot. A search on *wine* revealed a lot of files, but no .wine folder anywhere on the computer, inside or outside of chroot. And yes, I told the file manager to include hidden files and folders. I also searched manually in chroot, but no .wine folder.

I would have installed it in 64-bit, but the only thing listed in Synaptic is wine-doc. Documentation is not of much use without the application. However, wine was listed in Synaptic32 and that is how I installed it.

So it's somewhere in chroot. But where?

---

### Post by lutosdemayo on 2006-02-06
You can download winetools in winehq.org or install through synaptic. This will help you to configure the .wine directory in /home/user/ . You can compile it yourself and it doesnt require root permission. If you compile it yourself you can just type wt on the run application. This will help you out in installing dcom98 and internet explorer 6 and a lot of  other things to get you started. It will also put the the option open with WINE windows emulator when you right click a *.exe program.

---

### Post by John Jason Jordan on 2006-02-06
[QUOTE=lutosdemayo]You can download winetools in winehq.org or install through synaptic. This will help you to configure the .wine directory in /home/user/ . You can compile it yourself and it doesnt require root permission. If you compile it yourself you can just type wt on the run application. This will help you out in installing dcom98 and internet explorer 6 and a lot of  other things to get you started. It will also put the the option open with WINE windows emulator when you right click a *.exe program.[/QUOTE]
Thanks for the suggestion, but:

1) winetools is not listed in Synaptic32 (or 64-bit Synaptic).
2) I've never compiled anything and have no idea how to do that. Sounds seriously complicated. I'm new to Linux trying to learn it as I go along. But midterms are coming up and time is getting tight. 
3) I looked at winehq and perhaps winetools is something I should pass on anyway. For one thing, as you noted, it says it automatically installs Internet Explorer <puke>.

I can't believe Wine is this complicated. 

Right now the only thing I want to do is install Pegasus Mail under Wine. I have downloaded an .exe file which is really a self-extracting zip file.

---

### Post by RAOF on 2006-02-06
Run "winecfg" from a terminal.  That'll set up your wine environment, give you a ~/.wine directory, etc.

Then, run "wine /path/to/the/downloaded/pegasusmail.exe" from a console.  That will run the .exe, and (should, if it works in wine ;)) install the program.

And finally, the oblicatory: "Why are you trying to run Pegasus Mail under wine?  What does it do that a linux native mail client doesn't do?!"  ;)

---

### Post by lutosdemayo on 2006-02-06
[QUOTE=John Jason Jordan]Thanks for the suggestion, but:

1) winetools is not listed in Synaptic32 (or 64-bit Synaptic).
2) I've never compiled anything and have no idea how to do that. Sounds seriously complicated. I'm new to Linux trying to learn it as I go along. But midterms are coming up and time is getting tight. 
3) I looked at winehq and perhaps winetools is something I should pass on anyway. For one thing, as you noted, it says it automatically installs Internet Explorer <puke>.

I can't believe Wine is this complicated. 

Right now the only thing I want to do is install Pegasus Mail under Wine. I have downloaded an .exe file which is really a self-extracting zip file.[/QUOTE]

Its not that really hard compiling winetools anyway. To install WineTools extract the archive in a temporary directory and call
"./install" as user "root". WineTools will get installed at
/usr/local/winetools. If you want to have it somewhere else, change $BASEDIR
in wtXXXjo and findwine. Execute by typing (Not as root!) "wt" on a shell.

More instructions are listed in inside the tarball. Why dont you try to give it a shot and see how it goes and come back here to for more if you have anymore problems. Plus it will help you to install a number of supported programs with ease.

Remember it does not install internet explorer immediately. you have the option to install it but remember that a lot of windows programs do depend on internet explorer to function properly.

---

### Post by John Jason Jordan on 2006-02-06
[QUOTE=RAOF]Run "winecfg" from a terminal.  That'll set up your wine environment, give you a ~/.wine directory, etc.

Then, run "wine /path/to/the/downloaded/pegasusmail.exe" from a console.  That will run the .exe, and (should, if it works in wine ;)) install the program.

And finally, the oblicatory: "Why are you trying to run Pegasus Mail under wine?  What does it do that a linux native mail client doesn't do?!"  ;)[/QUOTE]
I tried "winecfg" and got "unknown command."

As for Pegasus the scene is this: I have a Windows 2000 desktop on which I still do more than half of my work. Linux is on my newly acquired laptop, which I got in order to learn Linux and also because I needed a computer to use at the university. Hence, I will continue to use Pegasus on the desktop computer, and that is where I will archive saved e-mails. The laptop will be set to leave all e-mails on the server. I just need to check during the day while at school so I can read anything important. If it's an important e-mail I will re-download it and save it later on the desktop.

Shortly after I got the laptop Mozilla came out with Thunderbird. "Cool!" I thought. "I can switch to Thunderbird and use it on both computers." Ah, but not so fast young Linux tyro! It turns out Thunderbird does not see all the messages on the server. And this happens with all three of my e-mail accounts, and on both the Linux and Windows versions. And I have tried the latest version and whatever is causing it is still not fixed.

So then I tried Evolution. Not bad, but it can't access one server at a time. It has one "Send/Receive" button and you have no choice but to retrieve from all servers at once, and to send all e-mails queued as well.

Following that I tried several other native Linux e-mail programs but they all want to download from all servers at once as well. This is just not acceptable. One of my accounts receives hundreds of e-mails a day, but none are critical. I don't want to have to wait for all those messages while at the university -- I can peruse those at home in the evening.

So that's why I want to run Pegasus under Linux.

Unfortunately, this is the end of the thread for me. This morning I uninstalled Wine. I don't really want to run it in chroot anyway. And I'm getting behind in my classes, so I'm calling a halt to any more software configuration issues. As for an e-mail client, I'm going to delete the big e-mail account from Evolution and put up with Evolution's limitations for now.

Thanks to everyone who offered suggestions and help. Maybe over spring break I can revisit this issue.

---

### Post by octowaters on 2007-06-12
> **RAOF said:**
> Run "winecfg" from a terminal.  That'll set up your wine environment, give you a ~/.wine directory, etc.

Then, run "wine /path/to/the/downloaded/pegasusmail.exe" from a console.  That will run the .exe, and (should, if it works in wine ;)) install the program.

And finally, the oblicatory: "Why are you trying to run Pegasus Mail under wine?  What does it do that a linux native mail client doesn't do?!"  ;)

Pegasus Mail will do FAR FAR MORE than anything created in any linux native mail client will do, As you seem to have doubts about this, I suggest you spend some time outside your linux cocoon and search for all the dope about the merits of Pegasus Mail. Amongst the comments, you will come up with the fact that since 1991 PMAIL has the most powerful filters of any mail client written even today, that is to say 2007.

Have a look... you will be surprised. What you and others could do is convince David Harris to port his mail client to Ubuntu, PCLPinuxOS as it will improve the all linux users mail capabilities. 

Evolution, Thunderbird, Sylpheed, Sylpheed Claws are just pathetic in comparison to what PMAIL offers and shows the user.

Ah, yes, David Harris makes his programme available for free. He sells the manuals, id yoiu want one, if not use it and get your help from the list. He also sells support. In reality Mr Harris has been doing from the start what (over 10 years ago) what the Open Source Community does, but, it seems, he has never got into a linux distribution to realize that he could do the same as he does in Windows. A great pity!:(:(

---


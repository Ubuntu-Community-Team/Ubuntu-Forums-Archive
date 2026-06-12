---
title: "Window's modem for Ubuntu?"
date: 2006-01-25
forum: Desktop Environments
---

### Post by Doc504 on 2006-01-25
I installed Ubuntu 5.10 in my old wins 98/2nd--running both os's:confused:.  Does anyone have any idea as to if this old win98 modem can be detected by Ubuntu?=; or, if not, what type of modem for Ubuntu, could be installed,  so I can get online?
Thanks.

---

### Post by linuxden on 2006-01-25
I take it you are running a a laptop, if so linux has enormous problems running "winmodems"...(these are the modems in laptops, they are just micro chips not real  modems...) the makers of these chips are notoriously bad at releasing drivers for them under linux...

[http://linmodems.org/](http://linmodems.org/)

is the place you want to have a look at first if it is the case...

---

### Post by ddtmsa on 2006-01-25
[QUOTE=Doc504]I installed Ubuntu 5.10 in my old wins 98/2nd--running both os's:confused:.  Does anyone have any idea as to if this old win98 modem can be detected by Ubuntu?
[/QUOTE]

Hi Doc504,

The linmodems site already suggested is a good starting point for information. It should be possible to get your modem working in Ubuntu, though it would be best if you thought of it as a mini-project. As I take it, you are dual booting win98/ubuntu, you can use win98 to get online and access sites and downloads; win98 uses a FAT32 filesystem and ubuntu can read/write to the windows files, provided you mount the windows disk (very easy via a faq). 

First thing to do is find exactly what make/model of modem you have, using either scanmodem, or via windows control panel, and search the manufacturer's website for unix (probably debian based) drivers.

Took me less than 5 days from total newbie to getting online ... huge buzz of personal satisfaction when I managed it!

---

### Post by linuxden on 2006-01-25
Doc504,

After rereading my original post, i realise how pessimistic it was.

As ddtmsa says in his post it is possible to get winmodems to work under linux, just a little more work than under windows... And you will be so proud and have such a feeling of exhiliration when you finaly hear it speak to the ISP's server....

---

### Post by Doc504 on 2006-01-26
Thanks for that info.  I should have indicated that I'm using a desktop computer that has a HSP 688T Fax Modem.  I have both wins98/2 nd and Ubuntu os.  and understand that I can set-up a C:\temp file on the wins os than download--"SCANMODEM" which I  could copy to my "Linux account"--it is this point that I'm lost.  How is this done?:confused: 
Is this command (cp /mnt/msdos/temp/scanModem.gz) typed in the TERMINAL of ubuntu?

---

### Post by ddtmsa on 2006-01-27
In order to mount a drive in Ubuntu, you first have to find what it is named in the partition table. Type

> 
sudo fdisk -l


and look for the FAT32 (windows) partition eg /dev/hda3

To mount the disk, type
> 
sudo mkdir /media/windows
sudo mount /dev/hda3 /media/windows/ -t vfat -o umask=000


An icon directing you to your windows files should now appear on your desktop.

Another comment .gz files are zipped files, bit like winzip .zip files, use gunzip to unpack them

I suggest you look at the site [http://ubuntuguide.org](http://ubuntuguide.org) which has alot of useful hints and tips on how to do all these sort of things

---

### Post by Doc504 on 2006-01-27
Thanks for that help.  Both my computer tech person firend that is helping me get connected to the internet,  and I are new to linux.   He felt that he needed linux drivers for the  HSP688T Fax modem that the old win98 computers has, but is having problems trying to find them.:confused: 
We were wondering where we are typing these "sudo fdisk" command:confused: --is it in the TERMINAL COMMAND of ubuntu?

---

### Post by linuxden on 2006-01-27
[QUOTE=Doc504] --is it in the TERMINAL COMMAND of ubuntu?[/QUOTE]

Precisely,

You can get hold of it in applications > Accesories > Terminal

---

### Post by ddtmsa on 2006-01-27
[QUOTE=Doc504]He felt that he needed linux drivers for the  HSP688T Fax modem that the old win98 computers has, but is having problems trying to find them.:confused: 
[/QUOTE]

Please look at my reply to the second thread you started asking this same question, it is not the manufacturer of the modem that is needed but the chipset it uses.

---

### Post by Doc504 on 2006-01-28
What we couldn't figure out was that on the Ubuntu guide it states--"if you see a bluish box, this means you have to execute the commands in Terminal mode (Applications -> System Tools -> Terminal) or use the content of that box as mentioned in some other instructions.":confused: 
But if you do go to Applications--System Tools--
you can NOT find--TERMINAL.
Like you state--you have to go to--"applications > Accesories > Terminal"
That did cause us to go in a "loop".
Maybe some one could change that.
\\:D/ 
We still can't do the ppp config in TERMINAL:evil: 
but still keep trying.:neutral:

---

### Post by ddtmsa on 2006-01-28
[QUOTE=Doc504]We still can't do the ppp config in TERMINAL:evil: 
but still keep trying.:neutral:[/QUOTE]

Ok, time for a bit of a confession; I quickly tried to get ppp config and pon to work and failed. But method I've outlined works robustly if you go througt the system -> administrator -> networking route. After configuring your dial up modem whenever you want to go online you just select the option and then activate it. I've no idea why this one option works but no others, but hopefully this will also work for you!

As for the 'blue boxes' in the ubuntuguide, that is just their styling to distinguish between information and (in blue) the commands you should enter into the terminal window ... as time goes by, I'm betting you will find openning a terminal window will  be one of your first operations after booting up!

---

### Post by Doc504 on 2006-01-30
We feel we are getting over our heads.
When we downloaded the scanModem, where do we open this?
We keep getting something about disk series.

---

### Post by linuxden on 2006-01-30
hey dude do you have access to a external modem?? 

It might ve a hell of a lot quicker for you... Its been a few days you guys been working at it... 

otherwise follow the instructions in linmodems.org... they are complete...

---

### Post by az on 2006-01-30
HSP usually means a PCtel modem....

---

### Post by Doc504 on 2006-01-31
Any particular type of external modem we could use?:confused: 
Thanks!:p

---

### Post by ddtmsa on 2006-01-31
[QUOTE=Doc504]Any particular type of external modem we could use?[/QUOTE]

From what I can work out, most exteral modems are USB modems. And from what I've read, getting a USB modem to work is even harder than getting a winmodem to work. No personal experience of this, so would be happy to be proved wrong by somebody with more knowledge.

If it is possible for you, I would suggest getting a broadband connection (I considered this briefly before getting my winmodem to work) as broadband is almost universally supported out of the box by ubuntu.

If you are dual booting and have no immediate need to get online with ubuntu, then I would suggest you continue playing around. You will only learn more and more about linux/unix, it is a fun learning curve if you've got the time. Reason for mentioning this, was having had to sign off on another individual who gave up on ubuntu over this issue. 

After re-reading the thread, you still haven't mentioned want sort of modem chipset you have. I know you are running Win98, but on XP and Windows Millenium it is very obvious to find out what the chipset is:

Please try in Windows (or the best approximation to this for your OS)

Start -> Control Panel -> Device Manager -> Modems

This should list the necessary information to tell you where to look for drivers,
in my case the gives the following information

Intel(R) 537EP V9x DF PCI Modem

which is how I know I had to search the Intel website for 537EP drivers.

---

### Post by kevinmthor on 2006-01-31
hi forum,

i posted on another thread but want to ask a question here. i can't download anything to my computer because i can't dial out. how can i get the modem information without downloading anything? is this possible? 

i havn't tried my USB with my ubuntu install yet, does that have issues?

k

---

### Post by linuxden on 2006-02-01
Doc if your desperate to get ubuntu + Internet, then any analogue modem should work... out of the box.... you then need to connect through 

```
 System > Administration > Networking (then you select a PPP connection...)
```

Otherwise the joy (and frustration) of learning to use the winmodem might be an alternative....

---

### Post by Doc504 on 2006-02-01
Thanks for all the help--this is a real cool forum for help.  You all have been great!  Think I'll play around with:p  Ubuntu for more Linux experience and than try either the winmodem setup or an external modem. \\:D/

---

### Post by ddtmsa on 2006-02-01
[QUOTE=Doc504]Thanks for all the help--this is a real cool forum for help.  You all have been great!  Think I'll play around with:p  Ubuntu for more Linux experience and than try either the winmodem setup or an external modem. [/QUOTE]

What a wonderful post, I guess for me it also sums up what I like about this Ubuntu world. I'm still at the playing around stage, which happens whenever my schedule allows. Good luck and even more importantly have fun ... and when enlightened, take a little time whenever you can to help the next generation :-)

---

### Post by Lunixfanboy on 2006-02-01
[QUOTE=kevinmthor]hi forum,

i posted on another thread but want to ask a question here. i can't download anything to my computer because i can't dial out. how can i get the modem information without downloading anything? is this possible? 

i havn't tried my USB with my ubuntu install yet, does that have issues?

k[/QUOTE]
To get the information on which chipset your modem is using, lspci is your friend. ls (list) pci devices, hence lspci, will tell you all the pci devices that were found on boot up. In a terminal/console, typing lspci and looking for communications device will give you the chipset (e.g. Agere, Lucent, PCTel, Rockwell, Conexant, etc). Once you know that, you can look at the linmodems list and find out how close or how far you are from support. By the way, Zoom and Actiontec make real PCI modems, but they cost around 50-60 USD, since they DO have all the pieces of a real modem.

---

### Post by linuxden on 2006-02-02
Hey,

Instead of using ```
lspci
``` you could download "scan modem" from linmodems.org and that will tell you what you need to install and do (ie setup) if you need to install anything.... (you could get lucky...) ;o)

[http://132.68.73.235/linmodems/index.html#scanmodem](http://132.68.73.235/linmodems/index.html#scanmodem)

---

### Post by Lunixfanboy on 2006-02-02
[QUOTE=ubuntulifestyle]Hey,

Instead of using ```
lspci
``` you could download "scan modem" from linmodems.org and that will tell you what you need to install and do (ie setup) if you need to install anything.... (you could get lucky...) ;o)
[/QUOTE]
Save that lspci is already present without having to connect to the internet, and doesn't require a windows download and then transfer to the Linux side of things of a file to run.

---

### Post by linuxden on 2006-02-03
Scan modem will put Doc504 in the right direction to getting his modem working it actually tells you the driver you need to use to get your modem to work... Now if you assist Doc504 in installing his modem untill the end then by all means saving 5 minutes and downloding scan modem is defo worth it...

Doc504 has been trying to get his modem up for the past week... Whats 5 minutes in the right direction...?? Scanmodem was made for a reason..!

whatever you decide good luck!

---


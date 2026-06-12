---
title: "Guidance for beginning installation"
date: 2007-05-21
forum: Desktop Environments
---

### Post by rdcmmnst on 2007-05-21
I'm sure you guys get a bunch of these everyday so thank you in advance.

My situation is I just bought an older A21m IBM laptop off of ebay. It was shipped to Kansas, at the moment I am situated in Russia and will not be in Kansas until The middle of june. Here in russia, I have high speed internet with unlimited bandwith, in Kansas I have dial-up . I would like to be able to download either an iso with a bunch of applications on them or find a place where i can download individual applications..but i'm not for sure which applications to download. Or how to go about doing that. I'm experienced with windows but completely new to linux. I feel comfortable tearing a computer apart..but command line interfaces seem kind of intimidating. 

So i guess if you could guide me to a batch download of applications or sites with compiled drivers. 

Also i've read so many book reviews on beginning with Linux but most of them seem to start with the very basic "this is your computer" or the very complex linux administration.  What books would you recommend. 

I'm open to anything really I just don't want to get to the laptop and find that i don't have a necessary component

Laptop specs: 700mhz, 200 meg ram, 20 gig drive..not much else was stated..it has windows ME on it.

---

### Post by aysiu on 2007-05-21
You can create your own ISO:
[http://aptoncd.sourceforge.net/screenshots.html](http://aptoncd.sourceforge.net/screenshots.html)

---

### Post by rdcmmnst on 2007-05-21
Apton sounds like you have to use Linux to download the applications..

Sorry i did not specify I am running a Win XP SP2 Box

Apton "APTonCD is a tool with a graphical interface which allows you to create one or more CDs or DVDs (you choose the type of media) with all of the packages you've downloaded via APT-GET or APTITUDE, creating a removable repository that you can use on other computers"

---

### Post by rdcmmnst on 2007-05-22
Well..i don't know if this was the correct place to post or not but any advice either about the book or what apps and drivers i could download would be helpful 

thank you

---

### Post by lhuser on 2007-05-22
Well, usually, you could get the applications from Synaptic, once you install it. However, your case seems like you would like the software. AptonCD is for Linux, AFAIK, and I don't know if there is a Windows version. My personal opinion is to look through bittorrent to find Ubuntu software CDs. Make sure they're up to date! If you don't, you might get stuff for Ubuntu 4 or something!

I ain't experienced, but I'm using theories and thinking power, so I can help you.

---

### Post by rdcmmnst on 2007-05-22
Thanks for the reply, i'll try the bittorrent idea, do they need to be for 7.04 only or can they be for the 6.xx versions as well?

---

### Post by rdcmmnst on 2007-05-22
sorry for the double post but i just couldn't find any cd or dvd iso's of general programs..maybe i'm not going about this the right way. I just dont want to be disapointed when i get to my system and it might not work because i don't have the right software.

---

### Post by aysiu on 2007-05-22
The only existing ones I know of are for 6.06 (Dapper) or 5.10 (Breezy):
[https://ubuntuplus.bountysource.com/](https://ubuntuplus.bountysource.com/)

---

### Post by rdcmmnst on 2007-05-22
Will these bonus cd's work with feisty or should i just stick with dapper or breezy for now. Is feisty a better place for me to start?

---

### Post by aysiu on 2007-05-22
Mixing and matching versions isn't good.

Honestly, your best bet, if you're going to burn any ISO is to burn the regular DVD:
[http://cdimage.ubuntu.com/dvd/current/](http://cdimage.ubuntu.com/dvd/current/)

The DVD has the entire Main and Restricted repositories. More details here:
[http://www.ubuntu.com/community/ubuntustory/components](http://www.ubuntu.com/community/ubuntustory/components)

Then install the Ubuntu DVD while you're still in Russia and download through [Synaptic Package Manager](http://www.psychocats.net/ubuntu/synaptic) as many programs as you can.

---

### Post by rdcmmnst on 2007-05-22
I would love to install and download apps while i can, but at the moment the laptop is on a different continent and i am not on a computer where i can do that, would it be possible to use the live boot option then use the apton application and download all the programs that i want and create the iso from there? or save the .deb (i think that's correct) files to a flash drive. will the files be configured to the specific computer or will they work on the laptop that is in america as well?

---

### Post by aysiu on 2007-05-22
Oh, I gotcha! Well, you can use the DVD as a live session and download the programs--sure. It's going to be a little tricky, though, depending on how much RAM you have.

See, the live session runs completely off the DVD/CD and your computer's RAM. So anything downloaded or "installed" just goes into your computer's RAM. If you have only 256 MB of RAM, for example, you won't be able to "install" many programs.

There are a couple of ways to handle this:

1. If you have at least 512 MB of RAM, you can "install" one program at a time and after each "installation," move the .deb files out of /var/cache/apt/archives to the flash drive.

2. You can mount the flash drive to /var/cache/apt/archives so that all the .deb files download directly to the flash drive.

Once you have all your .deb files in one place (flash drive, DVD, whatever), you can copy them over to your other computer's desktop and then ```
cd ~/Desktop
sudo dpkg -i *.deb
```

---

### Post by rdcmmnst on 2007-05-22
The computer I am on right now has a gig of ram and 300+ gig of free space..so that's not an issue..


I know that i could just do an install of ubuntu on this computer i just really don't want to risk any files..but i think i might just end up doing that and then it would be easier to get the apps..seems like a neat feature for the future would to have a program that can get programs just like in ubuntu but save them and not have to execute them..but that's just my opinion :)..

I have read about an option called WUBI for installation directly from windows, or should i use the cd instead?

---


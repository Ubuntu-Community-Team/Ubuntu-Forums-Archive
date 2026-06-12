---
title: "Soon to be Linux user -- have some questions"
date: 2009-04-16
forum: General Help
---

### Post by GL_NORWAY on 2009-04-16
Hello people!

I'm soon to install Linux, either 8.10 or 9.04 depending on how long I can wait before starting to explore this new OS -- new to me anyway.


**Question 1:**

I'm trying to go from Windows to Linux, but I'm going to do it gradually. Actually I'll always be depended on Windows since I use some specific programs that is not available for Linux and will most probably never be. But in the long run, I plan to move most of my applications and use over to Linux because of security, privacy and open source freedom.

This is how I plan to do it in the beginning:

I got several physical partitions on my HD with several different Windows versions that I boot between using Partition Magic and its multi boot feature. I choose witch partition to boot next before I shut down the system, and when I boot or power up the system, it will boot on the chosen partition. I plan to install Ubuntu on the last and smallest partition to begin with, just to start out and try to learn it and get used to it.

So booting from any windows partition to the Ubuntu partition will not be any problem since Partition Magic will recognize any Linux partition and I can just choose one before I boot my system or shut down.

But, how do I boot back to any of the other Windows partitions from Ubuntu?


**Question 2:**

How is Ubuntu like when it comes to privacy? E.g. if more than one person is using the computer and you want to keep your sessions private and keep it from logging your activities like remembering passwords, addresses, documents, locations, etc etc.


Thanks for any feedback or help! I look forward to trying this OS! :)

---

### Post by stalkingwolf on 2009-04-16
you can set up multiple users so each user has their own account.  Then those accounts can only be accessed by that user.

> choose witch  over the years i have known many Witches of
many different beliefs.  Never run into a choose witch before though.

:D

---

### Post by SkyIsFalling on 2009-04-16
> **GL_NORWAY said:**
> So booting from any windows partition to the Ubuntu partition will not be any problem since Partition Magic will recognize any Linux partition and I can just choose one before I boot my system or shut down.

But, how do I boot back to any of the other Windows partitions from Ubuntu?Disclaimer: I haven't used Boot Magic, try at own risk, back up first etc.

I'd suggest replacing the Partition Magic boot loader with grub, the default Ubuntu boot loader. During setup your existing Windows installs will be detected and added to grub. When you boot your computer, grub will display a menu that lets you choose between Ubuntu and your other Windows installs. At this point, stop using Partition Magic for selecting boots.

> **GL_NORWAY said:**
> E.g. if more than one person is using the computer and you want to keep your sessions private and keep it from logging your activities like remembering passwords, addresses, documents, locations, etc etc.

You can configure multiple user accounts just like in Windows. Ubuntu also has a "Guest session" feature suitable if you wanted to let someone use the computer for a while without worrying they'll snoop on your stuff.

> **GL_NORWAY said:**
> Thanks for any feedback or help! I look forward to trying this OS! :)

Good luck!

---

### Post by SkyIsFalling on 2009-04-16
> **stalkingwolf said:**
> you can set up multiple users so each user has their own account.  Then those accounts can only be accessed by that user.

  over the years i have known many Witches of
many different beliefs.  Never run into a choose witch before though.

:D

With a name like GL_NORWAY I'm guessing English is a second language. Amusing nonetheless :)

---

### Post by atomizer on 2009-04-16
> **SkyIsFalling said:**
> 
I'd suggest replacing the Partition Magic boot loader with grub, the default Ubuntu boot loader. During setup your existing Windows installs will be detected and added to grub. When you boot your computer, grub will display a menu that lets you choose between Ubuntu and your other Windows installs. At this point, stop using Partition Magic for selecting boots.


I second that.

With Grub you can choose the OS you want at boot time, instead of shutdown-time.

---

### Post by paradigm2 on 2009-04-16
Hello.  I can help a bit with Question 2.

Linux uses permissions and owners of individual files and directories.  Each user can have their own unique user id and password to log in.  If configured correctly this will help keep privacy.

However, the best way to keep privacy is to encrypt the files.  Using truecrypt ([http://www.truecrypt.org/](http://www.truecrypt.org/))  is a one really nice way to do this.  It works on both windows and linux.  So you could in theory create say a FAT32 data partition encrypted by truecrypt and then work with it in either windows or ubuntu.  And the security is that without the passphrase to decrypt it, no other user will be able to see what is on the encrypted partition.  This si the ultimate way to keep privacy.

If you do not encrypt, in theory anyone with physical access to your hard drive can potentially view your data no matter what permissions you set.  This is true in both windows and linux.

Having separate logins will help to keep things such as accessed documents and websites visited private.  Linux is a true multi-user operating system.

PS- I highly recommend installing 9.04 now over 8.10, even though it is technically beta.  It is so close to release tha tit might as well be stable.  Also as upgrades are released in the next week or two it will become an official stable release anyway.  Installing 8.10 will mean that you are far behind a lot of the improvements that have been made, especially with hardware support and bug fixes.

---

### Post by paradigm2 on 2009-04-16
> **stalkingwolf said:**
> you can set up multiple users so each user has their own account.  Then those accounts can only be accessed by that user.

  over the years i have known many Witches of
many different beliefs.  Never run into a choose witch before though.

:D

Okay, let's make it even and you can translate the post into native norsk without any errors of any kind. :) j/k

---

### Post by GL_NORWAY on 2009-04-17
> **stalkingwolf said:**
> 
  over the years i have known many Witches of
many different beliefs.  Never run into a choose witch before though.

:D

LOL! :D It was my auto spelling in MS Word that messed up. At least I have something to blame. :P

----------

Anyway, thanks everyone for answers and tips! I still have some questions though:

Firstly, I didn't get any answers on how to adjust the privacy settings in Ubuntu -- e.g. where to disable logging and such. I know that this isn't strictly necessary since Linux have a decent user login system, but nevertheless I'm just curious about how this works compared to Windows XP which I use now.

Secondly, the GRUB boot system in Linux -- since I'll be installing Ubuntu on the fourth and last partition on the disc, having three other XP installs, will GRUB put itself in the main boot record and always be activated even if I'm not booting to the Ubuntu partition? And will it be left there and work if I choose to uninstall Ubuntu?

Thirdly, and this may sound really stupid but forgive my lacking knowledge of cryptography, but how safe is TrueCrypt? I see that it only uses 128/256 bit algorithms. I have DriveCrypt now for Windows and it supports Triple Blowfish 1344bit algorithm. It’s not that I'm living in China or something, but again I'm just curious.

Thanks again for your kind help! :)

---

### Post by GL_NORWAY on 2009-04-21
I'm just bumping this thread _once_ to see if there are anyone who could contribute to my questions in my last post above. :)

---

### Post by CatKiller on 2009-04-21
> **GL_NORWAY said:**
> How is Ubuntu like when it comes to privacy? E.g. if more than one person is using the computer and you want to keep your sessions private and keep it from logging your activities like remembering passwords, addresses, documents, locations, etc etc.

Each user's settings are kept in their respective Home folders. There's no reason why any user should need to see what's in another user's Home folder. If it isn't set like that by default, it's pretty easy to do.

Ubuntu has a centralised "recent files" list. This is kept in each user's Home folder as ~/.recently-used. If you don't want the files you've recently accessed to be logged, make this file read-only. There's also a history of commands that you've run on the command line. This is stored in each user's Home folder as ~/.bash_history. You can turn this off as well.

Stuff that you do in a browser will be logged by that browser. As far as I know, all browsers come with the option to turn that logging off. Certainly Firefox, the default browser, does.

Really, if another user cannot see the contents of your Home folder, they won't see anything of what you, as a user, have done. However, there is a super-user, called *root*, who can manipulate any file on the computer. Users in the admin group are able to temporarily assume root powers with the sudo command. If there's someone that you don't want to be able to see things on the computer, don't put them in the admin group. But then if you were that concerned about what people would do with your computer you wouldn't give them physical access anyway.

---

### Post by chong67 on 2009-04-21
I use Vmware on all my Linux.  That way I can have both worlds without worry about partioning the hard drive.

---


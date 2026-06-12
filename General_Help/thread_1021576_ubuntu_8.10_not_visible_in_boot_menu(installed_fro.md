---
title: "ubuntu 8.10 not visible in boot menu(installed from Windows 7)"
date: 2008-12-25
forum: General Help
---

### Post by Dudeeeeee16 on 2008-12-25
Hey people! Help a fellow confused guy here will ya?I'm a big supporter of the linux community and I like linux and the promise it brings.I ran Ubuntu 7.10 roughly a year or two back but switched back to windows out of pure dependency of games and yahoo messenger(no,pidgin isn't a good alternative,and neither is Gyach Enhanced).Anyway the whole "installing inside windows is genius!".I am now running a windows 7 machine,installed wubi,gave 30 gigs of space,everything went well,and prompted me to restart where NORMALY i would have logged into Ubuntu.Right?So I restart and it loads directly into windows,and if I force the boot screen to appear,ubuntu isn't checked.I only have windows 7 there.Looked under windows system startup settings only to see that windows can't see Ubuntu.sorry for my bad english ppl but I'm sleepy as hell.....The question is: HOW CAN I MAKE UBUNTU APPEAR ON MY BOOT SCREEN WITHOUT SWITCHING BACK TO VISTA?(windows 7 is basickly vista,and everything from vista works on 7,the only difference is that win 7 runs more smoothly).By now I'm sure ur bored reading this,but I didn't see this problem anywhere,but bare with me,this is my first post)
                                Greets from Romania

---

### Post by dad3 on 2009-01-02
This happened for me too.....

Please anyone give a solution for this.

---

### Post by whero on 2009-01-02
I would like to know as well.

---

### Post by hyperdude111 on 2009-01-02
This also happened to me BUT I FOUND A SOLUTION.

To start with you need to boot from the ubuntu live cd.
go to terminal and type 

"sudo grub"
"grub> find /boot/grub/stage1"

That should return your Ubuntu partition in the form of (hdX,Y), use that:

grub> root (hdX,Y)
grub> setup (hd0)
grub> quit

This will restore your original ubuntu grub loader. When you re-boot windows 7 will be gone but you can fix it.

Boot into normal ubuntu again and go to terminal.

"sudo gedit /boot/grub/menu.lst"

A large text file will open and paste this at the bottom (leave a 2 line space from the last entry)


title		windows 7 beta (Loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

This should work it did for me.

if it doesn't work where you see the line "root (hd0,0)" try replacing the second zero with a 1,2,3,4,5,6,7 and so on until it works.

Good Luck

---

### Post by ithanium on 2009-01-02
i also had the same problem :|

---

### Post by bradthewanderer on 2009-01-02
Why would you even mess around with Windows 7 at this point in betas?

---

### Post by ithanium on 2009-01-02
> **bradthewanderer said:**
> Why would you even mess around with Windows 7 at this point in betas?

I wanted to try something new :D

---

### Post by k3n85 on 2009-01-11
From the command:
"sudo grub"
"grub> find /boot/grub/stage1"

Nothing was returned.  When trying to guess the X and Y values (tried hd0,0) Since Ubuntu is installed on the C:\.

grub> root (hdX,Y)
grub> setup (hd0)
grub> quit

The setup says it can't mount the drive.  For some reason it doesn't make sense to just have a 10 GB folder on the C:\ and have it mounted.  

Thanks for the advice...let me know if you have more information.

---

### Post by BinaryBrother on 2009-01-15
I am having the same issue, and

"grub> find /boot/grub/stage1"

Doesn't find anything...

Comp Specs:
Windows 7 Build 7000
AMD Phenom Tri-Core 2.8ghz
3GB DDR3
Asus Mobo

It appears that Windows 7's boot manager works just a little differently than Vista's. I know the answer simply lies in the usage of the Win7 boot manager, if we could somehow force Wubi into Win7's boot, then we could fix this problem... :(

Yes we are using a BETA OS, but Build 7000 isn't all that unstable and its memory management makes Vista look like a failed OS...Kinda makes me remember Windows ME...

Windows ME Vs. Windows XP
      Like
Windows Vista Vs. Windows 7

Don't believe me? Give it a try... and VMWare does not do it justice.

---

### Post by RealG187 on 2009-01-15
You have Windows 7, is that out now? I want it!

Sorry if I am changing the topic... :(

---

### Post by BinaryBrother on 2009-01-15
[http://www.microsoft.com/windows/windows-7/beta-download.aspx](http://www.microsoft.com/windows/windows-7/beta-download.aspx)

Yes... It's available... and LEGALLY at that... ;)

---

### Post by RealG187 on 2009-01-16
Is it free?

---

### Post by endrit10 on 2009-01-16
Yes its free, its a open beta, why don't you just read the website, if you did you would know that....

---

### Post by RealG187 on 2009-01-16
I read it now. It sucks you have to make an account.

I hate hotmail. Back when I thought hotmail was the only email provider I tried to signup for an account and it was giving me a hard time, I decided email wasn't for me (even though I am tech savy, even back then when I was a kid) until I found out about Yahoo....

---

### Post by ithanium on 2009-01-17
> **RealG187 said:**
> I read it now. It sucks you have to make an account.

I hate hotmail. Back when I thought hotmail was the only email provider I tried to signup for an account and it was giving me a hard time, I decided email wasn't for me (even though I am tech savy, even back then when I was a kid) until I found out about Yahoo....

just create an account and download it, it will not take you more than 5 minutes to signup:P

---

### Post by RealG187 on 2009-01-17
I "forgot" my login (I am sure I typed it in right and did the correct one but it wouldn't let me in) and it said I exceeded the limit of live accounts I can make (even though I only made one, one that I cannot use).

When I made my account I put "email@hotmail.com" and it gave an error, i put "email@m.com" and it worked, shouldn't that be the other way around. It said I had no inbox. But I guess I didn't need one, just the login...

Finally it went (I didn't make an inbox, cuz it wanted me to verify my ownership of the email adress "email@m.com" which doesn't exist (that's why I am trying to make it).

After I gruelling 2 hours I finally got it...

This is why I hate making accounts, something always goes wrong, you enter an invalid username or password or "fail" at the captcha, even though that was an a, despite the fact it was illegible and fiends can write better.

Then you have to fill out most of the form again because of one letter, like you wanted to do it the first time.

Why did hotmail have to be barred from [bugmenot](http://bestwikiever.wikidot.com/bugmenot)?

---

### Post by Draky on 2009-01-20
In Vista, to install 8.10, you had to put Grub on Linux boot partition and not in MBR and then in vista, you use EasyBCD to crate another entry in Vista Boot Manager.

I did the same in Windows 7 but when I choose "ubuntu entry" in the boot manager of 7, it fails...

So, until someone finds the "trick"... you have to wait for...

and please, no offtopic here : we're not interested in your life, it's not MTV, it's Ubuntu Forums...

---

### Post by bogdan2412 on 2009-01-20
[https://bugs.launchpad.net/wubi/+bug/318135](https://bugs.launchpad.net/wubi/+bug/318135)

Filled a bug here, maybe you guys can say this affects you too, so maybe it gets bumped up as importance

---

### Post by Zach.Town on 2009-01-21
I'm also having trouble with this :/ any fix yet?

---

### Post by Orange___Man on 2009-01-24
> **Zach.Town said:**
> I'm also having trouble with this :/ any fix yet?
The answers to various ways to dual boot are here:
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by Yownanymous on 2009-01-24
Hey look, Microsoft are once again being pathetic and trying to deter people from Linux! Mind you, at least Mr Torvalds hasn't had to sack 5 thousand people.

I knew the economic downturn plus Vista (aka Fail OS) would kill Microsoft. Bit off topic, I know, but Microsoft are EVIL.

---

### Post by gnuvistawouldbecool on 2009-01-25
I've done this with a true, partitioned install and GRUB installs from the live cd.  The issue here is that the /boot/grub/stage1 is located on the virtual disk, not a real partition, so grub can't find it or can't write to it, as far as I know.  However, I think that isn't the problem, because though wubi does go through grub, it uses the windows bootloader first.  Since the wubi root.disk will have been on the windows partition, as long as you upgraded rather than reformatted the windows partition the system should still be there.  So, to get Wubi to work you'll need to edit the windows bootloader to include the wubi install again.  Since I have no idea how to do this in Vista/7, I'll leave you with these links:
[http://www.microsoft.com/whdc/driver/tips/debug_vista.mspx](http://www.microsoft.com/whdc/driver/tips/debug_vista.mspx)

[http://msdn.microsoft.com/en-us/library/aa468626.aspx](http://msdn.microsoft.com/en-us/library/aa468626.aspx)

---

### Post by seth556 on 2009-01-25
On the launchpad report I got these directions.

1. Install *buntu using Wubi.
2. Install EasyBCD.
3. Using EasyBCD, add an entry for Linux>Wubi; change the drive from C: if appropriate.
4. Copy files from the winboot folder that Wubi created (wubildr*, menu.lst) to the root of the drive.
5. Go into a command prompt with admin privileges.
6. Use bcdedit to change the path of the BCD entry created by EasyBCD for Wubi from the mbr file EasyBCD installed to the mbr file you just copied to the root of the drive. (bcdedit by itself first to get the ID, then bcdedit /set {...ID...} path /wubildr.mbr)

Worked well for me.

---

### Post by endrit10 on 2009-01-27
Seth your command for 6) is incorrect, it should look like this:

bcdedit /set {ID} path \wubildr.mbr

This is what mine looked like:

bcdedit /set {4853af9e-e5d7-11dd-94eb-a06e3547ab30} path \wubildr.mbr

I pressed enter and it said operation completed sucesfully so I am going to restart now and see if it works.
Thanks seth.

WHAT EVER YOU DO, DO NOT COPY AND PASTE MINE, YOU HAVE TO USE YOUR OWN ID.

---

### Post by endrit10 on 2009-01-27
Didn't worked for me, it took me to a ******* busybox

I get this error:

Ext2-fs error (device sda1): ext2_check_descriptors: Block bitmap for group 53 not in group (block 0)!
Ext2-fs: group descriptors corrupted!

---

### Post by cheapsaket on 2009-01-29
I had the same issue, here is how i resolved it.

I am sure there is a more straight forward way but this sufficed for me.

I downloaded EasyBCD and added an entry for Linux.
Then from the command prompt, I edited the entry using bcdedit /set {ID} path to point it to the right path.
Then I was able to boot into Ubuntu from Win7 boot menu.
HTH.

> **Dudeeeeee16 said:**
> Hey people! Help a fellow confused guy here will ya?I'm a big supporter of the linux community and I like linux and the promise it brings.I ran Ubuntu 7.10 roughly a year or two back but switched back to windows out of pure dependency of games and yahoo messenger(no,pidgin isn't a good alternative,and neither is Gyach Enhanced).Anyway the whole "installing inside windows is genius!".I am now running a windows 7 machine,installed wubi,gave 30 gigs of space,everything went well,and prompted me to restart where NORMALY i would have logged into Ubuntu.Right?So I restart and it loads directly into windows,and if I force the boot screen to appear,ubuntu isn't checked.I only have windows 7 there.Looked under windows system startup settings only to see that windows can't see Ubuntu.sorry for my bad english ppl but I'm sleepy as hell.....The question is: HOW CAN I MAKE UBUNTU APPEAR ON MY BOOT SCREEN WITHOUT SWITCHING BACK TO VISTA?(windows 7 is basickly vista,and everything from vista works on 7,the only difference is that win 7 runs more smoothly).By now I'm sure ur bored reading this,but I didn't see this problem anywhere,but bare with me,this is my first post)
                                Greets from Romania

---

### Post by endrit10 on 2009-01-30
Just run it in compatibility mode for Windows Vista.
It will work and install fine.
Ubuntu will come up on the Boot options too....

But I keep getting the busybox error, no matter what i do, i get busy ******* box.

---

### Post by RealG187 on 2009-02-24
> **BinaryBrother said:**
> [http://www.microsoft.com/windows/windows-7/beta-download.aspx](http://www.microsoft.com/windows/windows-7/beta-download.aspx)

Yes... It's available... and LEGALLY at that... ;)

I downloaded Windows 7 here before the stopped providing it for download (I think the pirate bay has it) and am wondering, does the beta version expire? I heard it expires when a certain date hits.

---

### Post by eBrY on 2009-02-26
Worked like a charm. Thank you. Now I have 2 concerns. 

1.) How do I adjust the rather long 10 second wait inside the Ubuntu boot after selecting Ubuntu it asks if I want to go into the menu, which I would never have a need to do. I would like to set it to like 2 or 1 second to decrease boot time. Where would I adjust this? I am totally new to Ubuntu/Linux so thorough instructions needed. Would I have to use that Grub thing?

2.) Will installing a future build of Windows 7 wipe out the main fixed boot menu or will it leave it intact? The instructions are pretty clear and easy to follow. Still a hassle. Also, will the install of a new Windows 7 build upgrade mess up because of the modified boot so I can't boot into either OS? That would be a nightmare for me. I only have 1 notebook.

Please provide any feedback. Thanks.

> **seth556 said:**
> On the launchpad report I got these directions.

1. Install *buntu using Wubi.
2. Install EasyBCD.
3. Using EasyBCD, add an entry for Linux>Wubi; change the drive from C: if appropriate.
4. Copy files from the winboot folder that Wubi created (wubildr*, menu.lst) to the root of the drive.
5. Go into a command prompt with admin privileges.
6. Use bcdedit to change the path of the BCD entry created by EasyBCD for Wubi from the mbr file EasyBCD installed to the mbr file you just copied to the root of the drive. (bcdedit by itself first to get the ID, then bcdedit /set {...ID...} path /wubildr.mbr)

Worked well for me.

---

### Post by ntiller on 2009-03-07
> **cheapsaket said:**
> I had the same issue, here is how i resolved it.

I am sure there is a more straight forward way but this sufficed for me.

I downloaded EasyBCD and added an entry for Linux.
Then from the command prompt, I edited the entry using bcdedit /set {ID} path to point it to the right path.
Then I was able to boot into Ubuntu from Win7 boot menu.
HTH.

This worked great for me. Thanks! :D

---

### Post by paok4 on 2009-07-19
The fix is very easy my friend ... Look at this  [http://www.clububuntu.com/2009/01/how-to-solve-windows-7-and-ubuntu-810.html](http://www.clububuntu.com/2009/01/how-to-solve-windows-7-and-ubuntu-810.html) :P:P:P:P

---

### Post by Rob@ThePCWiz.info on 2010-01-30
Windows has always removed Ubuntu when you install it inside of windows, I don't know why you guys are just now figuring this out. I remember when I first started using Ubuntu, i installed it from inside windows, and i could use it fine, but if i ran windows once after, my Ubuntu installation would get ****** up.
 There is a very simple fix to this problem, simply create about, 6 - 20 GB worth of space in a seperate partition and install Ubuntu to that partition. You will then be given an option to run ubuntu or windows. Windows will not be able to **** this up for you. Have fun, happy coding

---


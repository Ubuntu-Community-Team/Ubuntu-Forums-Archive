---
title: "What did I Do Wrong"
date: 2009-05-03
forum: General Help
---

### Post by 2jessiejames on 2009-05-03
Good afternoon 
 I installed Ubuntu as a dual boot with my XP Pro Os several months ago and after installation found the problem that I'm about to describe .. Tried to figure it out, gave up, and went back to using XP professional till I had time to address the problem. 
 I now have time to continue with my exploration of the system, and have spent several hours trying to discover what  went wrong  ... to no avail. 
When I enter the system everything I type appears to be being encrypted. for example I type :
 
" How do I correct this problem?"           the following appears  ... Note the retypes of the word "this"
" Dr, er C jrp..jy ydco iprxn.mZ"            with the previous encrypting. 
                         fejr
                         u.hp

Addittionally When I boot up chosing  windows and use windows explorer to look for the second drive installed (there are two 160 gig drives installed) I cannot find any reference to the second drive that Ubuntu is installed on .... (No D hard drive)
 Could someone shed some light on how I have screwed up? 
                                        Thanks in advance for any information you may provide 
                                                                                  2jessiejames

---

### Post by blazemore on 2009-05-03
The 2nd issue is not really an issue, any more than "PS3 games won't play in my xbox!" is an issue.

The first issue sounds like you configured your keyboard incorrectly, try making sure the right type is selected in system->preferences->keyboard.

---

### Post by Wiebelhaus on 2009-05-03
I agree with the user above me , Your Keyboard is mis configured and the second issue is that Ubuntu is using either ext3 or ext4 filesystem which windows can't understand , there is an application that will enable you to browse the filesystem for NT based systems , but I cant recall the name , you'll need to use google to find it , now with the installation of "ntfs-3g" in Ubuntu you'll be able to browse and write to your NTFS partition.

Run this command to reconfigure your keyboard:

```
sudo dpkg-reconfigure xserver-xorg
```

***_Or with a modern GUI System>Preferences>Keyboard and make sure you have selected USA (Check screenie)_*** - [COLOR="Red"]suggested![/COLOR]

Now for browsing and writing to NTFS (Windows Partition) run this command:

```
sudo apt-get install ntfs-3g ntfs-progs
```

Cheers!

---

### Post by 2jessiejames on 2009-05-03
Thanks for everyone's Speedy reply! And everyone was on the mark! I had carelessly selected "Dvorak."
I must have done it prior to the name and password selection, making it a little more difficult to correct! As I had to decipher the password and name, before I could make the correction.
I'm sure I will be back many times as I have decided to try to move to a Linux based operating system .... while well versed in MS operating systems ... this is like having to learn a new language ..

                           Thanks again for your responses!:popcorn:

---

### Post by Wiebelhaus on 2009-05-03
> **2jessiejames said:**
> Thanks for everyone's Speedy reply! And everyone was on the mark! I had carelessly selected "Dvorak."
I must have done it prior to the name and password selection, making it a little more difficult to correct! As I had to decipher the password and name, before I could make the correction.
I'm sure I will be back many times as I have decided to try to move to a Linux based operating system .... while well versed in MS operating systems ... this is like having to learn a new language ..

                           Thanks again for your responses!:popcorn:

Yea it is mate , but yo. in 2005 after about 5 years of professional Windows platform related work , I endured about a month acclimation period but I dove right in full time once I educated myself on the benefits before even installing. I had decided that I was going to do this. I still work on Windows machines to pay the rent but I do it all with Linux!

Cheers mate and welcome aboard.

---


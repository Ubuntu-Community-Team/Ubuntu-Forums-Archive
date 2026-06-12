---
title: "Ubuntu for use in the field"
date: 2009-05-13
forum: General Help
---

### Post by apollocontrol on 2009-05-13
New user here, so please pardon my inexperience.

I've been really enjoying Ubuntu so far, and I read an interesting article recently about an archaeology group in the UK going entirely open source with their lab equipment, and using Ubuntu. This sounds great, but I wonder if it is really practical for the group I work with to do the same.

Here are the main issues I would be facing, if I were to try to prompt this switch.

Information is swapped between computers via flash drive. Viruses in Ecuador, where the project is located, are spread via flash drives and hard drives by simply replicating themselves onto all other drives as soon as they are plugged in. I know the virus didn't work on Vista, but it did on XP. Would this still be a concern on Ubuntu (or any linux) and if so are there any other work arounds (disabling autorun on flash drives for example)?

Many (if not all user but me) will have no experience with Linux, and may not be terribly computer literate. I am a newbie to linux but at least know the basics of how to use a computer. Can anyone say without that same bias that Ubuntu is user friendly enough for people who really have no clue or people who are just used to either Mac or Windows?

Currently the project uses Microsoft Office Access to catalog its data. Is there a comparable database program that works with linux? And if so, can that program read the project's existing Access files and work with them, or would I have to transfer the data over the hard way?

If you can think of any other pros or cons concerning using linux in an archaeology lab in Ecuador (being specific because hey, maybe it matters) let me know. Thanks in advance!

---

### Post by louieb on 2009-05-13
> **apollocontrol said:**
> Viruses 
Viruses are not a problem when you run Linux. (Their made for windows and won't run)
> **apollocontrol said:**
> 
Microsoft Office Access ...Is there a comparable database program that works with linux? ...Access files and work with them
There a plug ins for Open Office that will allow you use your access database data. 

Sounds like fun. Good luck.

---

### Post by jflaker on 2009-05-13
> **apollocontrol said:**
> New user here, so please pardon my inexperience.

I've been really enjoying Ubuntu so far, and I read an interesting article recently about an archaeology group in the UK going entirely open source with their lab equipment, and using Ubuntu. This sounds great, but I wonder if it is really practical for the group I work with to do the same.

It is practical and will keep costs low as you end up not needing to purchase OS and App licenses

> 
Here are the main issues I would be facing, if I were to try to prompt this switch.

Information is swapped between computers via flash drive. Viruses in Ecuador, where the project is located, are spread via flash drives and hard drives by simply replicating themselves onto all other drives as soon as they are plugged in. I know the virus didn't work on Vista, but it did on XP. Would this still be a concern on Ubuntu (or any linux) and if so are there any other work arounds (disabling autorun on flash drives for example)?

Virii do exist for Linux likely in the form of scripts.  Just like in Windows, you shouldn't just run something just because.  Scripts or binaries, know what your programs do before running them.
Virii, in order to do any real damage, need root access.  Unless you run stuff as root, the only real damage will be in your home folders.

> 
Many (if not all user but me) will have no experience with Linux, and may not be terribly computer literate. I am a newbie to linux but at least know the basics of how to use a computer. Can anyone say without that same bias that Ubuntu is user friendly enough for people who really have no clue or people who are just used to either Mac or Windows?

I have been using computers since Windows 3.0.  I transitioned through windows 3.0, 3.1, 3.11, 95, 98, 2000, XP, 2003 (server only), I played with Win7.....each time was a learning experience because things just didn't work the way it used to.  If you went from Windows to a MAC, you would see a learning curve there.  Ubuntu isn't MAC or Windows, so you will have a learning curve...once you get familiar with your OS, you will be right at home.....

> 
Currently the project uses Microsoft Office Access to catalog its data. Is there a comparable database program that works with linux? And if so, can that program read the project's existing Access files and work with them, or would I have to transfer the data over the hard way?
MySQL is an option and it can exist on a remote system or locally.  You would likely need to build some Web (PHP) applications around your data, but you had to build a gui in Access, didn't you?  You may need to tap some expertise if you can't do it yourself, but that would be the only down side.

> 
If you can think of any other pros or cons concerning using linux in an archaeology lab in Ecuador (being specific because hey, maybe it matters) let me know. Thanks in advance!
It isn't windows, it will never be windows and you should test all options before you dive into just switching.  Your current applications will likely not work in Wine, which is a program to allow most windows applications to run in Linux.  

Call others in your field that have made the switch and share with them your fears and ask if they will share their knowledge and maybe some application or application development help.

Remember, the free in Linux is not free as in free beer, but free as in you are free to change and adjust anything under Linux to your needs and/or liking.  You are free to share your changes, you are free to share Linux and any other open source application, in fact, it is encouraged.

---


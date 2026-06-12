---
title: "How to Idiot proof ubuntu?"
date: 2009-02-27
forum: General Help
---

### Post by mdgrech on 2009-02-27
When I first got started with ubuntu I dove right in without really knowing what I was doing.  There were a number of times were I totally messed up Ubuntu and had to reinstall.  

Now that I gotten to know ubuntu fairly well this isnt such an issue, but are there any ways to idiot proof ubuntu?

---

### Post by dcstar on 2009-02-27
> **mdgrech said:**
> When I first got started with ubuntu I dove right in without really knowing what I was doing.  There were a number of times were I totally messed up Ubuntu and had to reinstall.  

Now that I gotten to know ubuntu fairly well this isnt such an issue, but are there any ways to idiot proof ubuntu?

[LIST=1]
[*]Have a separate /home partition, then any subsequent reinstalls will not touch your user data.
[*]Save you installed package list with Synaptic-File-Save Markings, then you can read the file after a reinstall and install the same packages.
[*]Punch yourself in the face whenever you are tempted to break/change any system files.....   ;-)
[/LIST]

And remember, as soon as someone does make something "idiot proof", someone else builds a bigger idiot.....

---

### Post by mb_webguy on 2009-02-27
The best way to idiot-proof Ubuntu is not to tell the idiots about "sudo".  ;)

Generally, if you avoid doing things that ask for your password, it's really hard to mess things up.  Without superuser privileges, the only things you can affect are the settings in your home directory, which aren't hard to repair or restore.  It's also a idea, btw, to make backups of these settings every so often, in case you mess something up.  Since they're all just text files, backing up everything in an archive will only use between a few hundred KB to a MB.  Then, if you mess something up, you just delete the offending config file, and restore the backup copy from the archive.

dcstar's suggestion of a separate /home directory is also good, but not one you can easily implement without reinstalling Ubuntu.

---

### Post by darkmire on 2009-02-27
> **mdgrech said:**
> When I first got started with ubuntu I dove right in without really knowing what I was doing.  There were a number of times were I totally messed up Ubuntu and had to reinstall.  

Now that I gotten to know ubuntu fairly well this isnt such an issue, but are there any ways to idiot proof ubuntu?

I'd say it is more idiot proof than Windows and as idiot proof as most linux distros.  No OS is truly idiot proof and there is a learning curve involved. Anyone I encourage to try Linux I suggest that they use a live CD which allows them to try it on their machine which will then show where the issues are and give them chance to use it before taking the plunge. 

I personally like to try out new distros and other OSes using Virtualbox as you can do what you like without altering your computer's partitioning or doing anything else too drastic.  If I mess it all up, or just get fed up of playing around with it, I just delete the virtual machine, or revert to the last stable snapshot.  In work I have Windows XP on Virtualbox to run Windows stuff I still use (very little now) which obviates the need for dual boot and it's a much easier and stable solution than Wine or Crossover Linux.   This all assumes that Virtualbox is idiot proof, which of course it's not!

---

### Post by zvacet on 2009-02-27
@


As **dcstar** said having separate home partition is one way to protect your data and files.Read [this]("http://www.psychocats.net/ubuntu/separatehome") guide for making one.

> There were a number of times were I totally messed up Ubuntu and had to reinstall.

Why didn't you come here on forum and ask for help?

---

### Post by mike555 on 2009-02-27
If you are setting the computer up for another person , you can take things out of the menu's , that way they can't normally see them and wont click on them ..............

---

### Post by nothingspecial on 2009-02-27
> **mdgrech said:**
>  are there any ways to idiot proof ubuntu?

That`s not really the point, it sounds like you and I and probably most people learnt the hard way. But nothing teaches you about linux like breaking and fixing your system.

I have an old cheap laptop dedicated to this purpose.

However if you want to idiot proof it then use an account without sudo and only login to your main account when you want to sudo something.

---

### Post by meazz1 on 2009-02-27
> **dcstar said:**
> [LIST=1]
[*]Have a separate /home partition, then any subsequent reinstalls will not touch your user data.
[*]Save you installed package list with Synaptic-File-Save Markings, then you can read the file after a reinstall and install the same packages.
[*]Punch yourself in the face whenever you are tempted to break/change any system files.....   ;-)
[/LIST]

And remember, as soon as someone does make something "idiot proof", someone else builds a bigger idiot.....

Last option is the most useful one (lol).

---

### Post by wolfen69 on 2009-02-27
> How to Idiot proof ubuntu?
unplugging the computer is the only way to completely idiot proof it. ;)

---

### Post by Yellow Pasque on 2009-02-27
> **wolfen69 said:**
> unplugging the computer is the only way to completely idiot proof it. ;)
And even then.. the most dedicated "idiot" will make a thread somewhere asking why his/her cupholder no longer pops out automatically. Fellow "idiots" sympathetic to the cause will reply with a detailed walkthrough on how to use a paper-clip to get it to eject manually.

---

### Post by theozzlives on 2009-02-27
You can't idiot proof any OS. If someone wants to mess things up, they will.

---

### Post by mindaslab on 2009-02-27
I think the best way to idiot proof Ubuntu is to eliminate idiots. Give them a free Ubuntu CD, let them try, ask questions and experience it. They will soon no longer be an idiot.

---

### Post by miegiel on 2009-02-27
> **dcstar said:**
> [LIST=1]
[*]Have a separate /home partition, then any subsequent reinstalls will not touch your user data.
[*]Save you installed package list with Synaptic-File-Save Markings, then you can read the file after a reinstall and install the same packages.
[*]Punch yourself in the face whenever you are tempted to break/change any system files.....   ;-)
[/LIST]

And remember, as soon as someone does make something "idiot proof", someone else builds a bigger idiot.....

[LIST=1]
[*]I'm the kind of person who partitions manually so I stumbled over that 1 the 3rd time i installed ubuntu (probably in my 1st week)
[*]Thank you so much. :bow: I started making a script to "apt-get install" the stuff I want, this will save me a lot of time/effort keeping the script up to date.
[*]I've learned loads by breaking, repairing and (if necessary) reinstalling. Making mistakes is the most effective way to learn things, to me anyway.
[/LIST]

---


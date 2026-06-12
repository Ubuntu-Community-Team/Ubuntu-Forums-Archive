---
title: "Question on How to Get Hardy-Mariux Theme Working"
date: 2008-04-22
forum: Desktop Environments
---

### Post by Jbanicar on 2008-04-22
Hey,

I am following the readme that comes with the cool-looking Hardy-Mariunx theme for Hardy Haron, and I am unable to get the full theme functioning properly.  Could someone help clear this up for me?

These steps were followed to the best of my knowledge but ran into an issue:

	*GTk theme
Install this packages:
§ sudo aptitude install gtk2-engines-murrine
then copy "Hardy-Mariux" in your /home/.themes directory
Go in System -> Preferences -> Appearance->Customize then select "Hardy-Mariux" to choose this gtk theme.

Question: I could not find a /home/[username]/.theme or a /home/.theme directory.  Where is this located at? 

If you want sudo apps to run with Hardy-Mariux theme, just copy as sudo the Hardy-Mariux directory in your usr/share/themes directory.

Question: I know how to copy files, but I am used to using Red Hat that has a functioning root user.  How do I do this in Ubuntu? 

(see below)
jban@ sudo cp /home/jban/Desktop/Hardy-Mariux-1-1/Hardy-Mariux /usr/share/themes
[sudo] password for jban@ 
cp: omitting directory `/home/jban/Desktop/Hardy-Mariux-1-1/Hardy-Mariux'   (Why?)
jban@

Help please?  


Additionally, I am running Vista on this computer, and Ubuntu 8.04 RC1 is running in VM Workstation 6.0 (legal & registered).  How do I get the 3D Effects to work using Workstation 6.0 on Vista?  Is Vista even an issue?  I have seen some threads here on how to do it for Workstation5.0 running on WindowsXP.  Are these the same steps?  


Thank you!
-Jban

Here's the link: 
[http://mariuxv.deviantart.com/art/Hardy-Theme-75628261](http://mariuxv.deviantart.com/art/Hardy-Theme-75628261)

---

### Post by tedt on 2008-04-22
> Install this packages:
> § sudo aptitude install gtk2-engines-murrine
> then copy "Hardy-Mariux" in your /home/.themes directory

You uncompressed the file first right?

You could just open the Appearance dialog and drag-n-drop the file in

> Go in System -> Preferences -> Appearance->Customize then select "Hardy-Mariux" to >choose this gtk theme.

>Question: I could not find a /home/[username]/.theme or a /home/.theme directory.  Where >is this located at? 

you can also try ~/.themes

>If you want sudo apps to run with Hardy-Mariux theme, just copy as sudo the Hardy-Mariux >directory in your usr/share/themes directory.

>Question: I know how to copy files, but I am used to using Red Hat that has a functioning >root user.  How do I do this in Ubuntu? 

try sudo bash


>Additionally, I am running Vista on this computer, and Ubuntu 8.04 RC1 is running in VM >Workstation 6.0 (legal & registered).    

I am not sure that the accelerated desktop can work in a VM

---

### Post by Jbanicar on 2008-04-22
I'm sorry but could you be alittle more specific?

sudo bash? 
Did you mean "sudo bash cp ...." with the rest following?

Yes, the file is uncompressed.


And.... not sure if you read what I typed but ~/themes the same as /home/jban.... or /home in general.

---

### Post by tedt on 2008-04-22
> **Jbanicar said:**
> I'm sorry but could you be alittle more specific?

sudo bash? 
Did you mean "sudo bash cp ...." with the rest following?


No.  simply "sudo bash" at the command prompt will in Hardy drop you into a root shell

> **Jbanicar said:**
> Yes, the file is uncompressed.


And.... not sure if you read what I typed but ~/themes the same as /home/jban.... or /home in general.



yes ~/.themes == /home/jbanicar/.themes  ~/ == your specific home directory

so if you entered at the command prompt ls ~/.themes it should show the hardy theme you want to install

---

### Post by Jbanicar on 2008-04-22
It still continues to say:

cp Hardy-Mariux-1-1/Hardy-Mariux /usr/share/themes
cp: omitting directory `Hardy-Mariux-1-1/Hardy-Mariux'

Omitting directory??  I had cd'd into my Desktop so I didn't need to have that.


And what I meant about the themes directory, is that I can't find it.

---

### Post by tedt on 2008-04-22
> **Jbanicar said:**
> It still continues to say:

cp Hardy-Mariux-1-1/Hardy-Mariux /usr/share/themes
cp: omitting directory `Hardy-Mariux-1-1/Hardy-Mariux'


you might want to try:

sudo cp -r Hardy-Mariux-1-1/Hardy-Mariux /usr/share/themes/

when copying a directory and its contents you need the -r "recursive" flag

Also it is themes not theme.  

***sorry just saw that you had it right***

To fix the problem in the future you might want to tab complete

---

### Post by Jbanicar on 2008-04-22
Ok, I successfully copied it into the /usr/share/themes directory and also put it into the /home/jban.../.themes, but I have no option to select the theme at all in System Appearance/Customize.

I even followed the directions to download/install the Firefox portion by doing: 

	

[B]	*GTk theme
Install this packages:[/B]
§ sudo aptitude install gtk2-engines-murrine
then copy "Hardy-Mariux" in your /home/.themes directory
Go in System -> Preferences -> Appearance->Customize then select "Hardy-Mariux" to choose this gtk theme.
If you want sudo apps to run with Hardy-Mariux theme, just copy as sudo the Hardy-Mariux directory in your usr/share/themes directory.

        *Icons + Firefox Theme
To install the icons there are 2 ways:
1)Install the Tangerine.tar.tgz with Appearance Manager (System -> Preferences -> Appearance).
or
2)In terminal, run 
§ sudo apt-get install tangerine-icon-theme. Then Select in Appearance.
[B]
For the Firefox theme, run in terminal [/B]
§ sudo apt-get install firefox-themes-ubuntu
then open Firefox->Tools->Add-ons then select Tangerine theme, then restart Firefox.


No theme to select :(

I have to head out now, so I won't be able to reply further for tonight probably... but later on this morning :)

---

### Post by Jbanicar on 2008-04-23
I am back now, if you can reply further.

---

### Post by tedt on 2008-04-23
I am not sure what to say - if the uncompressed directory is in the .themes or /usr/share/themes then it should show up.  The only thing I can think of is if you look inside the directory it might contain a few different styles which would nned to be in their own directory for it to be seen

Yep the path is 

/Hardy-Mariux-1-1/Hardy-Mariux/GTK/Hardy-Mariux

that is the the GTK theme

so you would want to run 

cp ~/.themes/Hardy-Mariux/GTK/Hardy-Mariux ~/.themes

---


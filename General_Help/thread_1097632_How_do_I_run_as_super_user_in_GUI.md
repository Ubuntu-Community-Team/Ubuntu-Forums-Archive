---
title: "How do I run as super user in GUI?"
date: 2009-03-16
forum: General Help
---

### Post by myromance123 on 2009-03-16
I have an Ati binary I wish to install and I have tried through the terminal several times. Using sudo su wont work either. It keeps telling me permission denied.

```
./ati-driver-installer-9.2-x86.x86_64.run --buildpkg Ubuntu/hardy 
```

That's the code I'm trying to run in the terminal.
First it tells me permission denied. Then it tells me no such file or directory.

 the file is located on my desktop.

Its fullname is ati-driver-installer-9.2-x86.x86_64(2).run .
  See that (2) there? If I include that into the command it tells me :
bash: syntax error near unexpected token `2' .

If I double click the file it runs and then tells me that I need to be in super user to run it. I do not know how to be in super user whilst in the GUI.

Through the terminal its just a matter of using sudo or sudo su and inputting my password. How do I go around being super user in the GUI?

---

### Post by rasmus91 on 2009-03-16
```
Sudo ./ati-driver-installer-9.2-x86.x86_64.run --buildpkg Ubuntu/hardy
```

just type sudo in front of your command

If that doesn't work, its probably the directory which is wrong...

did you already set the Current path to where ever the file is? (i forget that sometimes :P )

Have you tried right clicking and choosing propeties, and then permissions?

---

### Post by sahabcse on 2009-03-16
Hi

Select login window in system>>Administration, there select security tap then un check Allow local system administrator login..

Or 

run #sudo bash 

it login to the root shel
then run
./ati-driver-installer-9.2-x86.x86_64.run --buildpkg Ubuntu/hardy

---

### Post by issih on 2009-03-16
As said above just prefix the command you want to run with sudo, and then type your login password when prompted in order to run a command as root. Ubuntu does not really want you to run as root, so using su is considered a no no.

There are ways around this, but ubuntu's whole security model is based on NOT being root, and just invoking roots powers when required, sudo stands for super user do, and that is what it is for.

Note that only members of the sudoers group can use sudo, so you can create users that have no root privileges at all.

The other part of your question probably boils down to having a somewhat dodgy filename with characters that are reserved in the bash (the terminal command environment) syntax. Any characters like that have to be escaped with a \ before them in order to be interpreted as just text and not a command to the shell.

In your case the easiest solution will be to start typing the file name something like:

```
sudo ./ati-dri
```

and then hit the tab key...this is linux's autocomplete feature and it will offer you any possible files that match what you have typed so far, and indeed just fill it in if there is only one. Fortunately for you, it will also do any necessary escaping of reserved characters.

Give that a whirl and see what happens.

Hope that helps.

P.S. if you wish to run a graphical application as root (e.g. the file manager nautilus) you can, but you should use the command gksudo not sudo as the prefix..so something like:

```
gksudo nautilus
```

will launch a file browser running as root. Obviously this is a dangerous beast, and you should close it as soon as you have performed whatever administrative action it is you need to do.

---

### Post by anaconda on 2009-03-16
OR

Boot to recovery mode )where you will be super user)

and type:
startx

It will start graphical user interface with root rights..

---

### Post by myromance123 on 2009-03-16
Thanks for the speedy replies doods.

  Yes I am in the right directory and I typed ls to make sure the file is in that directory.

 Typing sudo in front of ./ is a syntax error, thats a no-no by bash syntax.

I tried sudo bash, it's just the same as typing sudo su.
 Only now its **only** telling me there's no such file or directory (because I have to omit the (2) otherwise it throws a syntax error at me as mentioned above)

 Sahabcse, that login window method, what does it do?
I did it but I don't see any difference.
Do I have to log out and select it or something?
 I'm sure there must be a way to run the file in the GUI as super user.
Anyone know how?
  Right now I'm going to try and put the filename in these babies 'filename'  and we'll see if that allows the (2) to stay and function.

---

### Post by myromance123 on 2009-03-16
anaconda I do not know how to boot to recovery mode.
  Do I just access the menu after pressing esc at grub?
Select that mode from there?

---

### Post by sahabcse on 2009-03-16
Hi

Using my method you just log out from local user and try to login using root user and password. Then run the command using terminal.

If you have root password means in your terminal type

#su -

then type root user password

It login to root terminal.

Then executer your ./

---

### Post by issih on 2009-03-16
read my reply... :) that is the ubuntu way to solve this, rather than the brute force linux way. The others are quite correct that you can do those things, but its either hacking around the security model, or using the recovery tools to achieve a straight forward job that you should be able to do happily from a normal desktop.

Use sudo and tab complete, or gksudo nautilus...

N.B. no offence meant to anyone, if you want to run as root, go for it, but I don't think we should be advising someone who is clearly fairly green to do so..

---

### Post by myromance123 on 2009-03-16
Woot the single quotes saved the day!!

  Thanks guys :D
I solved it myself lol cos you guys gave me the courage to mess around with it xD

So I basically ran the command like this:
```
./'ati-driver-installer-9.2-x86.x86_64(2).run' --buildpkg Ubuntu/hardy
```


Its odd how those single quotes work. I'd think they'd be used for strings only, guess it forces bash to accept the filename as a string instead of a command or something :P

 Coolness! Alright on to the next part haha
The Atibinary ubuntu how to should have stated that from the beginning lol

---

### Post by theozzlives on 2009-03-16
Try:
sudo ~/Desktop/ati-driver-installer-9.2-x86.x86_64.run --buildpkg Ubuntu/hardy

---


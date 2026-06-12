---
title: "Installing Enemy Territory [Help!]"
date: 2007-04-28
forum: Gaming &amp; Leisure
---

### Post by hydroxph on 2007-04-28
I cant install because of "Failed Permissions", how can i install?

[IMG]http://i29.photobucket.com/albums/c291/hydroxph/GIFZ/1.png[/IMG]

[IMG]http://i29.photobucket.com/albums/c291/hydroxph/GIFZ/2.png[/IMG]

---

### Post by Stephen Howard on 2007-04-28
maybe run it as root (by prefixing 'sudo' to the start of the install command).

---

### Post by Stephen Howard on 2007-04-28
alternatively, change your installation path so that it installs inside your /home directory.  

I've installed mine in /usr/local without any difficulty.

---

### Post by kvonb on 2007-04-28
There are 2 ways to install ET, and for a lot of games for that matter.

If you run the installer by prefixing it with "sudo", it will install as a globally available application, ie it will be available to all users and accounts on your computer.

If you don't use the "sudo" prefix, it will give you permission errors when you try to install it into it's default folders because a standard user does not have permission to do that, so what you need to do is change the folder (whenever it pops up and asks for a folder location) to "~/enemy-territory".

The "~" means your home folder, and you can change "enemy-territory" to whatever you like.

If you do a "global" install, any maps/mods that you download will (I believe) be stored in a hidden folder in your home folder: "~/.etwolf".

Once installed you might like to add the ability to use teamspeak, or just to be able to play other sounds while ET is running.

To enable that, add this at the end of the do_start() section in /etc/init.d/bootmisc.sh:

```
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss

```Also, you will have to update punkbuster, download pbsetup.run from here:

[http://www.evenbalance.com/index.php?page=pbsetup.php](http://www.evenbalance.com/index.php?page=pbsetup.php)

And run it before you run ET.

---

### Post by lakersforce on 2007-04-28
> **kvonb said:**
> Also, you will have to update punkbuster

Any special reason for that you advise this?

---

### Post by kvonb on 2007-04-28
> **lakersforce said:**
> Any special reason for that you advise this?

...because you will be kicked from servers that require the latest version :).

If you're not getting kicked for outdated punkbuster then it doesn't matter I expect, but It was happening to me so I just thought I'd save you some hassles and recommend you do it beforehand.

---

### Post by lakersforce on 2007-04-30
Seems like you are right about that.

But I have problems installing it. No matter what I do I get errors. The name of the file is pbsetup.run. I tried out the following command with the following errors:

```
rune@rune-desktop:~$ sh pbsetup.run
pbsetup.run: pbsetup.run: cannot execute binary file
```

```
rune@rune-desktop:~$ sudo sh pbsetup.run
pbsetup.run: pbsetup.run: cannot execute binary file
```

```
rune@rune-desktop:~$ ./pbsetup.run
bash: ./pbsetup.run: Permission denied
```

```
rune@rune-desktop:~$ sudo ./pbsetup.run
sudo: ./pbsetup.run: command not found
```

I also tried running it by double-clicking on the file, with no avail.

What is wrong? :confused: :confused: :confused:

---

### Post by kvonb on 2007-04-30
You need to make it executable first. So open a terminal from the accessories menu and punch this in:

chmod +x pbsetup.run

Of course you will have to cd to the correct folder first :).

Now simply type:

./pbsetup.run

And it should now run.

You can also do that through Nautilus (or Konqueror if you use KDE) by right clicking on the file, selecting properties, and click on the permissions tab.  Then click on "allow executing file as program".

---

### Post by lakersforce on 2007-04-30
#-o

---

### Post by gardara on 2007-04-30
> **kvonb said:**
> You need to make it executable first. So open a terminal from the accessories menu and punch this in:

chmod +x pbsetup.run

Of course you will have to cd to the correct folder first :).

Now simply type:

./pbsetup.run

And it should now run.

You can also do that through Nautilus (or Konqueror if you use KDE) by right clicking on the file, selecting properties, and click on the permissions tab.  Then click on "allow executing file as program".

I did that and what I got was:
bash: ./pbsetup.run: Permission denied


any idea what's wrong?

---

### Post by Pox on 2007-05-04
You'll need to run it as root... try this:

```
sudo sh pbsetup.run
```

---

### Post by hydroxph on 2007-05-04
thx guy it worked, but now it freezes wen i try to go in a server or i cant downlaod the packages from the servers i join :(

---

### Post by gardara on 2007-05-04
> **Pox said:**
> You'll need to run it as root... try this:

```
sudo sh pbsetup.run
```

When I do that I get this


```
pbsetup.run: pbsetup.run: cannot execute binary file
```

:???:

---

### Post by DoktorSeven on 2007-05-04
sudo chmod 755 pbsetup.run
sudo ./pbsetup.run

---

### Post by gardara on 2007-05-06
> **DoktorSeven said:**
> sudo chmod 755 pbsetup.run
sudo ./pbsetup.run

I did:
sudo chmod 755 pbsetup.run
sudo ./pbsetup.run
sudo: unable to execute ./pbsetup.run: Permission denied


this is strange.... maby I'll download pbsetup.run again and see if it works then....

---

### Post by alexlex on 2007-05-16
I am havine the problem of not being able to get anysound at all no matter what i try. as soon as the intro screen  comes up i have no sound.

---

### Post by asipi on 2007-05-17
did you try this what mentioned above?-->
```
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
```

you have to do this as root

---

### Post by gbendotti on 2007-10-22
Hi All, my problem seems to be more related to Gutsy.

The pbsetup.run just does not execute.

The usual method just returns a new prompt.

:~/Downloads$ sudo ./pbsetup.run
:~/Downloads$ 

The other suggested method returns an error.

:~/Downloads$ sudo sh pbsetup.run
pbsetup.run: 18: Syntax error: "(" unexpected

This did work fine with Feisty.

Any clues as to how to get this sorted?

---

### Post by crane on 2007-10-22
Just for giggles have you tried running the full path name?
#sudo sh /home/you/Downloads/pbsetup.run

again make sure it is set to executable.
I have not run pbsetup under gutsy yet but will try this afternoon when I get home.

---

### Post by gbendotti on 2007-10-22
no joy, same thing:

sudo sh /home/you/Downloads/pbsetup.run
/home/me/Downloads/pbsetup.run: 18: Syntax error: "(" unexpected

I should say here that this is consistent on the two gusty machines I have here, the two feisty ones still work.

---

### Post by gbendotti on 2007-10-22
My problem was solved by some advice from evenbalance;
They said to run 
upx -d pbsetup.run

and try again.

I found out that it requires 

sudo apt-get install upx-ucl 

upx -d pbsetup.run
sudo ./pbsetup.run

It all works now.

---

### Post by iamah on 2007-10-22
> **gbendotti said:**
> My problem was solved by some advice from evenbalance;
They said to run 
upx -d pbsetup.run

and try again.

I found out that it requires 

sudo apt-get install upx-ucl 

upx -d pbsetup.run
sudo ./pbsetup.run

It all works now.
thanks so much!:guitar:

---

### Post by Stalafin on 2007-10-23
Ahh, sweet! Thanks a bunch!

But what is the reason that it works now and didn't before?

---

### Post by hans796 on 2007-10-28
Thanks. it helped for me too.. :)

---

### Post by poisonkiller on 2007-12-08
Anyone know, how can I UNinstall ET?

---

### Post by eexpress on 2011-04-03
pbsetup 3.2 gui
i add et to the list.

and still be kicked, says #20004.

---


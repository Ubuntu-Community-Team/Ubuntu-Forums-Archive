---
title: "Is it possible to share a World of Warcraft Folder/Game on A Vista/Ubuntu Dual Boot??"
date: 2009-04-02
forum: General Help
---

### Post by scrypt on 2009-04-02
Is it possible to Safely share The Folder containing WoW. 
Between Vista and Ubuntu
Even If I installed Ubuntu inside Vista using Wubi?

I have searched thoroughly for some clear concise instructions.
 But I have not been able to find any suited towards the level of understanding I have at present, of any Vista/Ubuntu folder sharing capabilities  

 I am not sure if it is even possible.

if it helps. WoW is in the public folder in my Vista set-up.

Has anybody had any experience of sharing files and folders between Vista and Ubuntu?

If so. Can you give me instructions. Or point me in the right direction on how to configure file, folder and  program sharing between Vista and Ubuntu??.

Thank's

---

### Post by mocoloco on 2009-04-02
I can tell you that on a Wubi install your windows partition is available as /host.  I don't have WoW and have never done this, but I assume you could go in to your wine folder, and have whatever folder you want to share be a link to the original folder on your windows partition.  So for example, ~/.wine/drive_c/Program Files/Blizzard/wow would be a link to /host/Program Files/Blizzard/wow.

---

### Post by scrypt on 2009-04-03
Okay thank's.

I get what you are saying, But I do not know how to create the link to the wow folder on my window partition.

How can I do this?

---

### Post by scrypt on 2009-04-03
HAs anyone had experience of this?

Can someone give me clear details plz?

---

### Post by scrypt on 2009-04-03
Quick bumpety bump.

anyone out there that can help out?

---

### Post by scrypt on 2009-04-03
I know the command to start Bluetooh adapter:

mark@ubuntu:~$ sudo toshset -bluetooth on

But i get this error output:

mark@ubuntu:~$ sudo toshset -bluetooth on
required kernel toshiba support not enabled.

I have installed toshet utility through synaptics  But im still having trouble utalizing it.

has anyone got any suggestions??

---

### Post by europa on 2009-04-03
i've run ventrilo from my windows partition on ubuntu before.  it's prob. safer just to re-install in ubuntu.

just go ahead and ditch windows. ;)

---

### Post by mocoloco on 2009-04-04
You can create a link with the GUI.  Right click, "Make link".  Move it to where it should be and rename it to the exact name as the original.  Or command line:
```
ln -s /host/Program Files/Blizzard/wow ~/.wine/drive_c/Program Files/Blizzard/wow
```

That's the link command (ln), make it a symbolic link (-s. Never forget this option!), then [Target] [Link name]

---

### Post by scrypt on 2009-04-04
Thanks for the reply mocoloco...

It might as-well be in Chinese.

I'm keen learner though if you wouldn't mind clarifying your last post for me?

Thank's

---

### Post by unutbu on 2009-04-04
mocoloco isn't on right now, so I'll take a swing at it:

Open a terminal (Applications>Accessories>Terminal) and copy and paste this from the web browser to the terminal:
```

ln -s "/host/Program Files/Blizzard/wow" "~/.wine/drive_c/Program Files/Blizzard/wow"
```

This command creates a symlink from "~/.wine/drive_c/Program Files/Blizzard/wow" to "/host/Program Files/Blizzard/wow". Note that you need quotation marks around the paths because there is a space in "Program Files". 

When wine looks for files in "~/.wine/drive_c/Program Files/Blizzard/wow", Ubuntu will show the files that are really in "/host/Program Files/Blizzard/wow". 

Here is an explanation of how to make symlinks using nautilus (the default Ubuntu file browser): [http://linux.about.com/library/gnome/blgnome6n6l.htm](http://linux.about.com/library/gnome/blgnome6n6l.htm)

---

### Post by scrypt on 2009-04-04
Hi unutbu

I tried the command in the terminal and got this output :-

mark@ubuntu:~$ ln -s "/host/Program Files/Blizzard/wow" "~/.wine/drive_c/Program Files/Blizzard/wow"
ln: creating symbolic link `~/.wine/drive_c/Program Files/Blizzard/wow': No such file or directory

---

### Post by unutbu on 2009-04-04
This means you do not have a directory called ~/.wine/drive_c/Program Files/Blizzard/

To make this directory, type
```

mkdir -p ~/".wine/drive_c/Program Files/Blizzard/"
```

Then try making the symlink again.

---

### Post by 3Miro on 2009-04-04
It depends. I have shared Heroes of Might and Magic, STALKER and Oblivion between windows and Linux, however, sharing Civilization seems to fail. Sometimes works sometimes not.

---

### Post by scrypt on 2009-04-04
okay I ran the commands but still the same output:-

mark@ubuntu:~$ mkdir -p ~/".wine/drive_c/Program Files/Blizzard

/"mark@ubuntu:~$ ln -s "/host/Program Files/Blizzard/wow" "~/.wine/drive_c/Program Files/Blizzard/wow"
ln: creating symbolic link `~/.wine/drive_c/Program Files/Blizzard/wow': No such file or directory

Do I need to configure wine in anyway??

Im sort of new to this.
But I'm a keen learner..

---

### Post by scrypt on 2009-04-04
I have taken a look at wine and there is a Blizzard directory that has appeared in the:-

C:/Program Files/Blizzard

But the Blizzard File/Folder is empty!

---

### Post by unutbu on 2009-04-04
Sorry scrypt, I seem to have jumped in over my head here.
I know how to make symlinks (yay) but am clueless about wine.
I thought you already had wine setup and just needed to symlink in WoW.

You probably need to install and setup wine first.
Hopefully, someone who knows more about wine can help you.
Maybe this page will help too: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154)

---

### Post by scrypt on 2009-04-04
No worries Matey.

Thank's for the help anyhow....

---

### Post by mocoloco on 2009-04-04
> **scrypt said:**
> Hi unutbu

I tried the command in the terminal and got this output :-

mark@ubuntu:~$ ln -s "/host/Program Files/Blizzard/wow" "~/.wine/drive_c/Program Files/Blizzard/wow"
ln: creating symbolic link `~/.wine/drive_c/Program Files/Blizzard/wow': No such file or directory

I just made up those paths as an example.  You'll need to find out the real ones.  Also I forgot to list it but you have to escape out spaces, so you put a backslash before them.  If you just use tab completion it will fill in the path as you go.
Apparently you need to install wow under wine first anyway.

---


---
title: "How do I become the owner???"
date: 2005-06-22
forum: Desktop Environments
---

### Post by braveerudite on 2005-06-22
I copy and edited a copy of " xorg.conf" file from the file system folder so I could change the the synchronization range line so I could view my monitor at a higher refresh rate.  I want to replace the original "xorg.conf" file with the copy I edited but would not let me because it says I'm not the owner. I'm logged to the only account that I made when I installed Ubuntu ....but how do I log in as the owner so I could have enough permision to change this filesystem file???

---

### Post by Dave_is_sexy on 2005-06-22
System > admin > users

show all > set root password

system > admin > login screen set-up

security > allow root login

login with "root" "password"

---

### Post by angkor on 2005-06-22
Oo dave, that is one terrible reply  [-X 

You don't need to log in as root to be able to edit xorg.conf.

Just use:

```
sudo gedit xorg.conf
```

to edit and:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf_bak
``` 

to make a backup first.

---

### Post by braveerudite on 2005-06-22
I will try that now... brb  THX

---

### Post by Kimm on 2005-06-22
I stronly suggest you dont use the "mv" command and then restart the xserver in this case ;-) , lets make that a "cp"!

[i]Edit:

I just noticed it said **first** ](*,) anyway... I still suggest using cp :-P[/i]

---

### Post by braveerudite on 2005-06-22
[QUOTE=angkor]Oo dave, that is one terrible reply  [-X 

You don't need to log in as root to be able to edit xorg.conf.

Just use:

```
sudo gedit xorg.conf
```

to edit and:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf_bak
``` 

to make a backup first.[/QUOTE]
 Where do I write this commands? (I'm a noob) Perhaps which of the 2 Terminals? or what is sudo?

---

### Post by Kimm on 2005-06-22
which terminal? ;-) 

doesnt mather at all, just use whatever is standard in your desktop, if your using gnome then use gnome-terminal, if KDE use konsole :)

[i]Edit again ](*,) :

Sudo is a command to allow your user root (Administrator) privelages, it means you can do anything to your computer basicly.

what you want to do is to move your edited file to the directory where the normal file is, open the terminal and type this (dont mind the #>'s):

> 
#>sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
#>sudo rm -f /etc/X11/xorg.conf
#>sudo cp <path to edited file> /etc/X11/xorg.conf


[/i]

---

### Post by braveerudite on 2005-06-22
I used the command "sudo gedit xorg.conf" and got this 

(gedit:28818): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
root@ubuntu:/home/braveerudite #


The xorg.conf file open but nothing was in it.....What happen? ](*,)

---

### Post by Kimm on 2005-06-22
That sounds wierd, never had that happen before.
make sure you still have the file there :-P if it is... perhaps a restart of the x-server?
or maby just try again...

Anyway, if you still have the edited file you dont have to do it that way, just follow the instructions in my last post :)

---

### Post by braveerudite on 2005-06-22
I used the command you told me sudo cp </home/braveerudite/Desktop> </etc/X11>

and got this: bash: syntax error near unexpected token `<'

---

### Post by Bandit on 2005-06-22
[QUOTE=braveerudite]I used the command "sudo gedit xorg.conf" and got this 

(gedit:28818): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
root@ubuntu:/home/braveerudite #


The xorg.conf file open but nothing was in it.....What happen? ](*,)[/QUOTE]

WTF?? I have never seen this error before in my life.... :? 
Was you in the directory where the xorg.conf is located?
Cheers,
Joey

---

### Post by Kimm on 2005-06-22
lol, yes that would also be one of the things you should check! lol

---

### Post by angkor on 2005-06-22
> **Kimm]I stronly suggest you dont use the "mv" command and then restart the xserver in this case  said:**
> Edit:

I just noticed it said **first** ](*,) anyway... I still suggest using cp :-P[/i]

 :wink: 

yeah, cp is good too :)

---

### Post by angkor on 2005-06-22
[QUOTE=braveerudite]I used the command "sudo gedit xorg.conf" and got this 

(gedit:28818): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
root@ubuntu:/home/braveerudite #


The xorg.conf file open but nothing was in it.....What happen? ](*,)[/QUOTE]

did you type the full path? 

sudo gedit /etc/X11/xorg.conf

---

### Post by angkor on 2005-06-22
[QUOTE=braveerudite]what is sudo?[/QUOTE]

if you put sudo in front of a command it executes the command with root powers. It prompts you for your user passwd.

---

### Post by Dave_is_sexy on 2005-06-22
To be fair, if you just want to edit a file as root, and want to avoid the command line (always a good idea until you get used to the environment), you can add a comand to the right click menu:

OPEN AS ROOT

Which would be perfect. 

copy - paste this code into terminal

```
gedit $HOME/.gnome2/nautilus-scripts/Open\ as\ root
```

copy-paste this text into that file and push 'save'

> for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
	gnome-sudo "gnome-open $uri" &
done

now copy-paste this code into terminal

```
chmod +x $HOME/.gnome2/nautilus-scripts/Open\ as\ root
```

Now you can right click on the file you want to edit, select 'scripts' and say 'open as root' to let you modify it  :smile: 

-------------------------------------------------------------------------------------
Info stolen blatently from: [http://www.ubuntuguide.org/#openfilesasrootviarightclick](http://www.ubuntuguide.org/#openfilesasrootviarightclick)

---

### Post by braveerudite on 2005-06-22
\\:D/ You are the man Dave... \\:D/  I'm such a noob to Linux but then again you gave me step by step instruction in how to get it done.  I am so greatful right now.... It worked just like Dave said.  Thank you so much.... It should be this simple by default to edit a systemfile without doing all those SUDO commands. Now I can after doing what Dave said. Cheers!!!!  Now How do I get my refresh rate up from 60 to 75....?

---

### Post by desdinova on 2005-06-22
[QUOTE=braveerudite]\\:D/ You are the man Dave... \\:D/ I'm such a noob to Linux but then again you gave me step by step instruction in how to get it done. I am so greatful right now.... It worked just like Dave said. Thank you so much.... It should be this simple by default to edit a systemfile without doing all those SUDO commands. Now I can after doing what Dave said. Cheers!!!! Now How do I get my refresh rate up from 60 to 75....?[/QUOTE]

Sudo is there to protect you from deleting/changing a file without realising it - and hosing your system.

I recommend you install the rute book to your system via Synaptic and read it - its an excellent guidfe on how Lonux behaves.

 It would be much better for you to learn the ways of sudo then blindly logging in as root all the time.

---

### Post by braveerudite on 2005-06-22
\\:D/ All solved Thank you all for your support!!! \\:D/

---


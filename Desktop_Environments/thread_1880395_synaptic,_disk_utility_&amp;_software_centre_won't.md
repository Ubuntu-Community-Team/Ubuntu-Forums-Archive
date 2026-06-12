---
title: "synaptic, disk utility &amp; software centre won't start/work"
date: 2011-11-13
forum: Desktop Environments
---

### Post by Jake the Peg on 2011-11-13
Hello,
I installed Xubuntu 10.10 on Dell Latitude D420 dual boot with XP.
All well at first including these programs, but after updates and adding programs, the following stopped functioning properly:
1) Synaptic - doesn't start from menu, only from terminal with sudo command.
2)Software center - starts but no response when pressing Install program. There is no password prompt when opening the program. When opened from terminal "sudo software-center" it works fine.
3) Disk Utility - opens, but no privileges to change anything.

The malfunctions seem related - no root privilege prompt, so need to use terminal with sudo command to start the programs in a functional mode.

Any ideas? Delete something from cache?

Thanks,
Jake.

---

### Post by ankspo71 on 2011-11-13
Hi
I think it could be a ownership permissions problem, or maybe "gksudo" got uninstalled or is not working. I think it would be the first problem though (ownership permissions).

Nothing inside your personal home folder should by owned by anyone but you (your username), so not even "root" should own your files. You can you check the permissions of files and folders in your home folder by using the following command in the terminal:
```
find -printf '%u %g\n' | sort | uniq
```

If the command returns "yourusername yourusername" (jake jake) then ownerships are fine.

But if the command returns "root root" or anything other than your username, then you will need to regain ownership of those files. The following command will use chown to change ownership of all files and folders recursively inside your home folder.

```
sudo chown -R jake:jake /home/jake
```
(replace jake with your actual Xubuntu username.)

Now try running Synaptic again from the start menu, or with the command "gksudo synaptic".

Also, using the "sudo" command with graphical applications can mess up permissions settings pretty bad in some cases. It is always best practice to open graphical applications with gksudo instead.

> Graphical sudo
You should never use normal sudo to start graphical applications as Root. You should use gksudo (kdesudo on Kubuntu) to run such programs. gksudo sets HOME=~root, and copies .Xauthority to a tmp directory. This prevents files in your home directory becoming owned by Root. (AFAICT, this is all that's special about the environment of the started process with gksudo vs. sudo). 
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Hope this helps.

---

### Post by Jake the Peg on 2011-11-14
Thanks for the suggestion which I tried:

darren@djh-D420:~$ find -printf '%u %g\n' | sort | uniq
darren darren
root root
darren@djh-D420:~$ sudo chown -R darren:darren /home/darren
[sudo] password for darren: 
chown: cannot access `/home/darren/.gvfs': Permission denied

So I get both my username twice and root root

The .gvfs is an empty hidden folder in my Home.

Thanks for any interpretation of this and/or suggestions,
Jake

---

### Post by Jake the Peg on 2011-11-14
I just retried this, and now get:

darren@djh-D420:~$ find -printf '%u %g\n' | sort | uniq
darren darren
darren@djh-D420:~$ 

So no root root after your suggested operation.

1) Synaptic still won't start from the menu.
1) Software center starts, but as before the Install button flickers and the "Free" work flickers to "installing" for 0.1 sec then goes back to Install (with nothing actually installed.

Both programs function normally after starting with gksudo.

I can live with starting these from the Terminal using gksudo... but it is a shame with a new install. 

Thanks,
Jake.

---

### Post by Jake the Peg on 2011-11-29
So, I found out what the problem was. I was deselecting too many startup applications. If I reselect them then I can access these programs directly from the menu as before. Something to do with keyrings probably...

---


---
title: "viruses?"
date: 2009-05-08
forum: General Help
---

### Post by JakeHinojosa on 2009-05-08
ive heard there are one or two viruses for linux, but do those viruses even affect your computer very much?

---

### Post by MysticalRiotCandy on 2009-05-08
At the most, they might infect your /home directory.  But unless you ran the virus on yourself at root, there's no way for it to escape that directory.  That's why we have sudo to use admin commands at user level.  For an example, running 'rm -rf' on your own account will not kill off your OS.  It will not be able to delete anything in /.  It will be able to delete files in ~/ if you set it to do so, but nothing else.  However, running 'sudo rm -rf' *will* delete every file in /.  The reason Windows machines are so prone to virus infections is because by default, Windows runs your user account at admin level.

However, viruses can still infect files that can infect Windows machines, so you should still install an AV software such as Clam to clean up files that you take to any other Windows machine.

---

### Post by colau on 2009-05-08
> **MysticalRiotCandy said:**
> At the most, they might infect your /home directory.  But unless you ran the virus on yourself at root, there's no way for it to escape that directory.  That's why we have sudo to use admin commands at user level.  For an example, running 'rm -rf' on your own account will not kill off your OS.  It will not be able to delete anything in /.  It will be able to delete files in ~/ if you set it to do so, but nothing else.  However, running 'sudo rm -rf' *will* delete every file in /.  The reason Windows machines are so prone to virus infections is because by default, Windows runs your user account at admin level.

However, viruses can still infect files that can infect Windows machines, so you should still install an AV software such as Clam to clean up files that you take to any other Windows machine.
Would you please tell how to install Clam antivirus for ubuntu?

---

### Post by _Purple_ on 2009-05-08
> **colau said:**
> Would you please tell how to install Clam antivirus for ubuntu?

```
sudo apt-get install clamav
```

---

### Post by colau on 2009-05-08
> **_Purple_ said:**
> ```
sudo apt-get install clamav
```
Thanks _Purple.

---

### Post by krendar on 2009-05-08
After installing clamav scan with:

```
clamscan -r /home/username
```

To scan that folder.

If you want a gui scanner I recommend you install

```
sudo apt-get install nautilus-clamscan
```

This will insert a right-click menu entry in Nautilus so that you got easy access to scanning files. I think you might have to log out and in again to enable the menu after installing.

---

### Post by x C0MMAND0 x on 2009-05-08
Check out the new AVG for Januty!

[http://techreviews.in/free-avg-anti-virus-for-ubuntu/](http://techreviews.in/free-avg-anti-virus-for-ubuntu/)

---

### Post by Wiebelhaus on 2009-05-08
> **colau said:**
> Would you please tell how to install Clam antivirus for ubuntu?

[BitDefender ]("http://ubuntuforums.org/showthread.php?t=1130400")It's not all free and open but it's the best. Download it and install the . run file:

```
sudo sh /home/yourname/location_of_file/Nameof.runfile.run
```

And follow the prompts.

Cheers.

---

### Post by sanozuke02 on 2009-05-08
i installed avg on my ubuntu but i cant see the application.. where can  i  find my installled avg?? i tried to find it in accesories but there's no avg their... help me pls......!!!???:(:(:(:(

---

### Post by mcduck on 2009-05-08
> **JakeHinojosa said:**
> ive heard there are one or two viruses for linux, but do those viruses even affect your computer very much?

Most Linux viruses that have ever existed have been just proof-of-concepts and newer existed in the wild. The few ones that really did spread targeted outdated software versions (most famous being Slapper which only worked on Apache servers that hadn't been updated for years).

So if you somehow managed to find a Linux virus it most likely wouldn't even work on your system. That means that until the situation changes your Linux machine is safe from viruses.

Many people recommend using antivirus scanner if you share stuff with Windows machines. in my opinion that's useless, if the Windows machine doesn't have working protection it's pretty much screwed, and if it does it's safe on it's own anyway.

Of course the situation is different if you are running e-mail server for corporate use or something like that, in which case it makes sense tho scan the stuff on the server instead of doing it locally on each user machine. Pretty much all Linux antivirus software is done for this purpose, to be used on mail servers to protect Windows machines. (exception being apps like Avast, that are marketed for home users with claims that you are not safe with Linux and should buy their program now before Linux viruses appear out of nothing and break your computer :D)

---

### Post by sanozuke02 on 2009-05-08
i just wanna make sure that my pc is secure from viruses... 

i already download and installed avg in ubuntu.. but I cant see the application of it.. 


thannks...

---

### Post by 3rdalbum on 2009-05-08
I've never heard of anyone actually contracting one of these supposed "linux viruses" since I've been a Linux user... and I became a Linux user in 2005.

Don't bother installing an anti-virus program. No Linux viruses have been created for years, and the old ones are no longer around (and wouldn't even work on today's Linux systems).

I believe AVG for Linux is a command-line program, but honestly, it will not protect your computer from anything. There is nothing to protect against!

---

### Post by x C0MMAND0 x on 2009-05-08
> **sanozuke02 said:**
> i installed avg on my ubuntu but i cant see the application.. where can  i  find my installled avg?? i tried to find it in accesories but there's no avg their... help me pls......!!!???:(:(:(:(

Run the graphical interface using the following command.

```

sudo avggui
```

This article shows how to work it.
[http://techreviews.in/free-avg-anti-virus-for-ubuntu/](http://techreviews.in/free-avg-anti-virus-for-ubuntu/)

---


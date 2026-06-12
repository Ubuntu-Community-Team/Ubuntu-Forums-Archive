---
title: "Change gnome-keyring password?"
date: 2006-04-09
forum: Desktop Environments
---

### Post by justinjstark on 2006-04-09
When I changed my user password in gnome, the gnome-keyring password did not change with it.  Any idea how to change it?

---

### Post by justinjstark on 2006-04-09
Nevermind, I found gnome-keyring-manager that allows me to change it all.

I'm going to uninstall it right away though because it seems that you can figure out the keyring passwords simply by opening it and clicking the checkbox "show passwords."  :???:

---

### Post by coldrick on 2006-04-12
Hmm. What I want to do is change the password to be used to access the default keyring.

Is there some way to do that?

Regards,
David

---

### Post by justinjstark on 2006-04-12
[QUOTE=coldrick]Hmm. What I want to do is change the password to be used to access the default keyring.

Is there some way to do that?

Regards,
David[/QUOTE]

Install gnome-keyring-manager.  Run it and there will be a "local password for user root."  Change that and it will change your keyring password.

IMO, if gnome is going to have something like a keyring (which I think is great), it also needs to have tools to be able to change keyring passwords built in.

---

### Post by coldrick on 2006-04-21
Nope - not on my system. No reference to anything but the passphrase for my WPA wireless and a couple of password from shared folders on other systems.

Wait a minute - perhaps if I change *my* password - that is, the one I use for sudo - that will become the password for the keyring. Have you enabled the root account on your system?

---

### Post by justinjstark on 2006-04-21
[QUOTE=coldrick]Nope - not on my system. No reference to anything but the passphrase for my WPA wireless and a couple of password from shared folders on other systems.

Wait a minute - perhaps if I change *my* password - that is, the one I use for sudo - that will become the password for the keyring. Have you enabled the root account on your system?[/QUOTE]

No root account, just sudo.  And I don't think changing the user password will change the keyring password because it didn't for me.  The whole reason I wanted to change the keyring password was because I changed my user password and then wanted my keyring pass to match.

---

### Post by ronmarley1 on 2006-04-21
[QUOTE=blaksaga]When I changed my user password in gnome, the gnome-keyring password did not change with it.  Any idea how to change it?[/QUOTE]
 Here's another solution:
Click on Places, Home Folder. You will then need to hit Control+H on your keyboard to view hidden files. (By the way, if you want to always view hidden files, you can click on Edit, Preferences and click the box in front of Show hidden and backup files.) Browse to the folder called .gnome2, and then to the folder called keyrings. Inside it is a file called default.keyring. Delete it and the next time you enter a site or mount with a password, it'll ask for a keyring password, and then you can set a new one.

---

### Post by justinjstark on 2006-04-21
[QUOTE=ronmarley1]Here's another solution:
Click on Places, Home Folder. You will then need to hit Control+H on your keyboard to view hidden files. (By the way, if you want to always view hidden files, you can click on Edit, Preferences and click the box in front of Show hidden and backup files.) Browse to the folder called .gnome2, and then to the folder called keyrings. Inside it is a file called default.keyring. Delete it and the next time you enter a site or mount with a password, it'll ask for a keyring password, and then you can set a new one.[/QUOTE]

Good tip; thanks.

---

### Post by ronmarley1 on 2006-04-21
[QUOTE=blaksaga]Good tip; thanks.[/QUOTE]
No problem, mon.

---

### Post by dfm21 on 2007-02-01
> **ronmarley1 said:**
> ...Home Folder. [...] hit Control+H [...] to view hidden files.[...] Browse to the folder called .gnome2, and then to the folder called keyrings. Inside it is a file called default.keyring. Delete it and the next time you enter a site or mount with a password, it'll ask for a keyring password, and then you can set a new one.

short: 
```
rm ~/.gnome2/keyrings/default.keyring
```
or backup:
```
mv ~/.gnome2/keyrings/default.keyring ~/.gnome2/keyrings/default.keyring.bak
```

Thank you ronmarley1! It works fine for me.

---

### Post by Fitzcarraldo on 2007-03-07
> **dfm21 said:**
> short: 
```
rm ~/.gnome2/keyrings/default.keyring
```
or backup:
```
mv ~/.gnome2/keyrings/default.keyring ~/.gnome2/keyrings/default.keyring.bak
```

Thank you ronmarley1! It works fine for me.



This did _not_ work in my case:

```
mv ~/.gnome2/keyrings/default.keyring ~/.gnome2/keyrings/default.keyring.bak
```


But this _did_ work in my case:
 
```
rm ~/.gnome2/keyrings/default.keyring
```


I believe that is because Gnome Keyring Manager looks for the file default.keyring in the keyrings folder and, if it does not find it, looks in other files in that folder. As the file default.keyring.bak is in the same folder, Gnome Keyring Manager prompts the user for the default password stored in that file, which is the same as the password one is trying to change in the first place!

So the solution is make sure the folder keyrings is completely empty. However, I still wanted to make a backup of the file default.keyring in case something went wrong, so I did the following:

```
mv ~/.gnome2/keyrings/default.keyring ~/Desktop/default.keyring.bak
```

Which also works in my case.

---

### Post by asimonelli on 2007-03-28
With Edgy, if you open the Keyring Manager, press F9 to display keyrings.  Then you have the option to delete the key ring.  Then you will create a new keyring and password when you use an application that works with the gnome keyring like nm-applet.

This is essentially the same thing as deleting the default.keyring file in ~/.gnome2/keyrings folder, but at least you're using a GUI, which helps to make sure you don't delete something else by accident.

---

### Post by ugm6hr on 2007-05-19
Works well. 

An icon in the taskbar which runs in terminal means I can delete the keyring with a single click.  

This ability to set things up the way you want is great.  And I'm realising how powerful XFCE is.  Wonder what else I could customise with GNOME/KDE...

---

### Post by PeeZz on 2008-01-06
> **ronmarley1 said:**
> Here's another solution:
Click on Places, Home Folder. You will then need to hit Control+H on your keyboard to view hidden files. (By the way, if you want to always view hidden files, you can click on Edit, Preferences and click the box in front of Show hidden and backup files.) Browse to the folder called .gnome2, and then to the folder called keyrings. Inside it is a file called default.keyring. Delete it and the next time you enter a site or mount with a password, it'll ask for a keyring password, and then you can set a new one.

And what if theat default.keyring file does not exists?
I have 2 *.keyring files but not a default.keyring.

---

### Post by ronmarley1 on 2008-01-07
> **PeeZz said:**
> And what if theat default.keyring file does not exists?
I have 2 *.keyring files but not a default.keyring.

Actually, the original posting goes back to before Feisty, so I believe my reply no longer fits for Gutsy.  There's a new applet on the System -->Administration menu called Keyring Manager.  That will allow you to add/delete keys and keyrings.

---

### Post by doug-M on 2008-03-04
Try this:

Install Seahorse key ring manager ([http://www.gnome.org/projects/seahorse/](http://www.gnome.org/projects/seahorse/))

You install it using:
[B]
sudo apt-get install seahorse[/B]

Then go to:  **Applications -> Accessories -> Passwords and Encryption Keys**
  (This will open seahorse)

Once in Seahorse do
  **Edit -> Preferences**
  Select the [ **GNOME Keyring** ] tab

It will ask for your old Master password and allow you to enter a new one.

---

### Post by matey3 on 2008-04-29
thanks for the info. I thought the keyring resided on the remote server I was trying to ssh to!
I deleted the passwords and now I get in fine!
thanks!

---


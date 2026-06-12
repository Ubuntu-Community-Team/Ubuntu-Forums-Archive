---
title: "How To Change Gnome Keyring Password?"
date: 2007-01-30
forum: Desktop Environments
---

### Post by dfm21 on 2007-01-30
Hi!

I want to change the password gnome-keyring wants from me every session.
It once asked me for a master password and I do not know how to change it.
Please help!

Felix

---

### Post by MystaMax on 2007-01-31
helo felix,

I'm actually having the same problem. I came across your thread before finding [this post]("http://www.ubuntuforums.org/showpost.php?p=943443&postcount=7"), by ronmarley. It explains how to remove the keyring file within your home folder.

[quote=ronmarley1]
 Click on Places, Home Folder. You will then need to hit Control+H on your keyboard to view hidden files. (By the way, if you want to always view hidden files, you can click on Edit, Preferences and click the box in front of Show hidden and backup files.) Browse to the folder called .gnome2, and then to the folder called keyrings. Inside it is a file called default.keyring. Delete it and the next time you enter a site or mount with a password, it'll ask for a keyring password, and then you can set a new one.
[/quote]

I'm trying it now...

---

### Post by MystaMax on 2007-01-31
yep, it worked for me too. But, renaming the file (for backup purposes) did not work for me.

From the CLI, I tried to rename the file to BACKUPdefault.keyring, but that didnt work. After restarting, it asked me for password, but it wouldn't accept my previous keyring password. It accepted a password, that I don't remember ever setting. So next time, I moved it to my home directory, and restarted. It then asked me to set a new keyring password. very nice.

hope it helps you too.

---

### Post by dfm21 on 2007-02-01
short: 
```
rm ~/.gnome2/keyrings/default.keyring
```
or backup:
```
mv ~/.gnome2/keyrings/default.keyring ~/.gnome2/keyrings/default.keyring.bak
```

Yep, works fine. Thank you for pointing me, MystaMax!

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

Yep, works fine. Thank you for pointing me, MystaMax!



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

### Post by abickerton on 2008-01-28
Use Gnome seahorse 

Here's the article that led me to the answer.
[http://sadamclemson.blogspot.com/2007/06/seahorse-gnome-keyring-integration.html](http://sadamclemson.blogspot.com/2007/06/seahorse-gnome-keyring-integration.html)

---

### Post by dfm21 on 2008-01-29
You could also try KDE. IMHO it is the better Desktop Environment and it's "Wallet" just works.

---


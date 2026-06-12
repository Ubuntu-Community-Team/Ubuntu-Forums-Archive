---
title: "Gnome apps don't start"
date: 2005-11-14
forum: Desktop Environments
---

### Post by Orval on 2005-11-14
I don't know why this happened, but gnome doesn't start anymore. After login in the screen turns black and after a second or so the login screen appears again.

Loggin in in KDE works, but I cannot run any gnome application (evolution, gnome-terminal).

When shutting down, I notice that gdm is not running, which probabely is the cause of the problems.

1. How can I restart gdm and make sure it starts automatically at login?
2. Any ideas about how this could have happened?

Thanx for the response.

---

### Post by tehwa on 2005-11-14
[QUOTE=Orval]1. How can I restart gdm...[/QUOTE]
```
sudo /etc/init.d/gdm restart
```
[QUOTE=Orval]and make sure it starts automatically at login?[/QUOTE]
This will probably resolve with a reconfigure. Terminal:
```
sudo dpkg-reconfigure gdm
```
[QUOTE=Orval]2. Any ideas about how this could have happened?[/QUOTE]
Could be many millions of reasons, GNOME's good like that. Likely to be related to a recent tweak to your system.

---

### Post by Orval on 2005-11-14
Thanks, tehwa, i'll try your suggestions.

---

### Post by Orval on 2005-11-14
Well, it did not work. I even reinstalled Ubuntu and the kubuntu-desktop all over again (formatting my /) and still got the same problem. Gnome won't start, and neither will gnome-applications (and some other like firefox) in KDE.

When I try to start evolution from the konsole I get:

```
(evolution-2.4:9661): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET  (widget)' failed
```


and when I start gnome-terminal from the konsole I get:

```
Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
```

Any ideas?

---

### Post by tehwa on 2005-11-14
Orval, did you keep the existing user (/home) files from the previous installation? Consider setting up a new user, and using that user to log into GNOME. This will give you an idea of whether it is a GNOME library error (system) or a user config error (possibly - it's worth a look).

If you are unfamiliar with the process of adding a new user, the command is:

```
sudo adduser
```
manual is helpful:
```
man adduser
```

---

### Post by autocrosser on 2005-11-15
A problem I had not long ago was very similar--I had just just changed my theme & all Gnome apps crashed--tried everything I could think of---no joy. I created a new user & had not a problem one, so--went back to my old user & deleted the theme I was using at the time the "crashes" started-----no more problem--I guess it was a "corrupted" theme--seems the only logical reason............

---

### Post by Orval on 2005-11-15
[QUOTE=tehwa]Orval, did you keep the existing user (/home) files from the previous installation? Consider setting up a new user, and using that user to log into GNOME. This will give you an idea of whether it is a GNOME library error (system) or a user config error (possibly - it's worth a look).
[/QUOTE]

Yes, i kept my home directory. So you must be right: it must be a configuration error. I will try to make a new user and see what it will bring. Is it enough when I delete installed themes as the new user? Or will they still be available as my original user account? Can't I just delete one or more (hidden) directories in my user account?

Anyway, I will make a new user account tomorrow and see what it will bring.

Autocrosser, I think you are right about the theme. I did install a couple of themes and did some other things after which the problems started. Strange though that installing Gnome themes distroys the system.

Thank you for your help.

---

### Post by autocrosser on 2005-11-15
I have root enabled in my system & went into the "Damaged" user account--moved the theme I thought was the problem out of the .theme directory & then logged out of root---logged in as my "normal" user & the problem was gone---I use root only when I REALLY need it--just glad I enable it for times like this:D
 
I'd go ahead with setting up a new user--if there is not a problem using Gnome apps in the new account---You can be sure that it is a .file problem--remember very carefully the steps up to the problem & remove them from you damaged account one by one--log in to the account after every change you make externally, otherwise you won't know what REALLY fixed it---

---

### Post by Orval on 2005-11-17
Well, I created a new account, which worked flawlessly. No problems there.

Then I deleted all of my ./folders and .files one at a time in mijn old account and try to log in, without any succes.

Then I copied all the ./folders and .files from my new account to the old account and tried to log in. Again, no succes.

Finally I decided to remove my old account and all the files,  and created a new one with the same name. Copied back all my non-./folders and files to the new account. Logged in and it worked again.

But no clue about what was wrong.

A new problem is that now the original first account is gone, the root password is also not working anymore. I have to give my new account root privileges in order to be able to perform root tasks. This is obviously a situation I do not want. Do I have to install Breezy all over again in order to restore the original situation?

---

### Post by Orval on 2005-11-18
First I tried to 

```

sudo passwd root

```

but that didn't do the trick. I was not able to perform sudo actions even I had the right to do so.

So finally I installed Ubuntu and the Kubuntu-desktop all over again and everything works fine now. I didn't particulaly enjoy it, but I learnt a lot about my new OS, which I still think is great. I can hardly describe the relief I feel having thrown off the shackles of M$ and proprietary software.

---

### Post by Orval on 2005-11-18
A new problem has come up.

I had several personal addressbooks in Evolution. After the reinstall I only see the original personal addressbook and the others are gone. It seems to be impossible to import the db-files of the other addressbooks. Is there a workaround? I am not looking forward to create the addressbooks all over again.

---

### Post by autocrosser on 2005-11-18
Sorry--I don't know about Evolution--I've been using ThunderBird--Am glad to see you came out the other side without much damage--If you still remember your root password-you can goto System>Administration>Login Screen Setup & in the Security tab "Allow Root to Login with GDM"--do not allow remote login! This will allow a way out if everything goes "bad"--WARNING!!! from that account you can edit EVERY file on the system--use it with extreme care & DO NOT be on the 'net in that account!! I use it to change permissions on files (the problem you had when you were swaping .files between accounts) & system things I find easier from there **note-I've been a Linux user for several years & am comfortable with root--do not use root as you main account, only as the "super user"**

---


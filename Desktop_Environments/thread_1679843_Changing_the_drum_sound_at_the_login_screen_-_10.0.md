---
title: "Changing the drum sound at the login screen - 10.04."
date: 2011-02-01
forum: Desktop Environments
---

### Post by Dalbelo on 2011-02-01
Step 1: Create an audio file in (.ogg) format name (system-ready.ogg).

Step 2: Open nautilus with root privileges by pressing ALT+F2 and typing:

gksudo nautilus

Step 3: Navigate to /usr/share/sounds/ubuntu/stereo/

Step 4: In this directory rename the current (system-ready.ogg) file to (system-ready.ogg.backup)

Step 5: Copy your custom (system-ready.ogg) file into this directory.

Step 6: Restart your computer and enjoy.

---

### Post by brian mcgee on 2011-04-30
This should work in 11.04 too. Also, just try renaming /usr/share/sounds/ubuntu/stereo/dialog-question.ogg

Or maybe removing the symlink /usr/share/sounds/ubuntu/stereo/system-ready.ogg

---

### Post by nightshadowfx on 2011-09-26
hi all trying to change my desktop login sound to one a made it's a .ogg but when i do the sudo I am unable to rename to original sound or even move it. any help would be nice thank you in advance.

---

### Post by tedrogers on 2011-11-03
Any idea how to get the login drum sound to work. Mine has not worked since installing 11.10.

I went through the list of ogg files in the directory mentioned above, and it's called the 'system-ready.ogg' file, this is the one that isn't playing at the login prompt.

---

### Post by debd on 2011-11-03
the file actually played at the login is desktop-login.ogg

---

### Post by tedrogers on 2011-11-03
> **debd said:**
> the file actually played at the login is desktop-login.ogg

I refer to the Ubuntu conga drum sound when presented with the login dialogue:

/usr/share/sounds/ubuntu/stereo/system-ready.ogg

The file you refer to:

/usr/share/sounds/ubuntu/stereo/desktop-login.ogg

...is the long choral angelic tune upon successful login.

---

### Post by debd on 2011-11-04
oh
I got a bit wrong :)

---

### Post by tedrogers on 2011-11-04
> **debd said:**
> oh
I got a bit wrong :)

Any ideas then? The one thing I miss is the system ready tone, calling me back to my computer :)

---

### Post by debd on 2011-11-05
there's a option 'play sound at login' in the Login Screen dialogue  System>Administration>Login Screen in 10.10

not sure what sound that points to and if that's available in 11.10 but may try out..

---

### Post by tedrogers on 2011-11-06
> **debd said:**
> there's a option 'play sound at login' in the Login Screen dialogue  System>Administration>Login Screen in 10.10

not sure what sound that points to and if that's available in 11.10 but may try out..

None of these options are available in 11.10, and anyway, they all point to the startup sound (the long angelic one) and not the system-ready sound (the conga drum bongs awaiting password input).

---

### Post by Frogs Hair on 2011-11-06
> **tedrogers said:**
> None of these options are available in 11.10, and anyway, they all point to the startup sound (the long angelic one) and not the system-ready sound (the conga drum bongs awaiting password input).

Here is a possible solution for 11.10 . Install the following. ```
sudo apt-get install dconf-tools 
```

Open from dash by typing dcon and proceed to org > gnome > desktop > sound and make sure event sounds is checked .

---

### Post by skey. on 2012-06-25
Like to thanks makes things different, easy to follow,
 Cheers

---


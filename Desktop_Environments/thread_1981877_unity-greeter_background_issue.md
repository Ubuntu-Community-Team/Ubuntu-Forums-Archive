---
title: "unity-greeter background issue"
date: 2012-05-17
forum: Desktop Environments
---

### Post by ckop64 on 2012-05-17
Unity-greeter does not follow the wallpaper set for my user. Under 12.04.

I have tried tracing this back, it seems like, that the wallpaper has to be under /usr/share/backgrounds in order to be "visible" for unity-greeter. 

The odd thing is, that for a different user on the same machine the greeter works just fine, and follows the wallpaper even if it's in the home folder of that user. 

I am completely stuck now, and the least thing I want to do is to create a new user and start everything over again.

Any help is appreciated!

---

### Post by ckop64 on 2012-05-17
I think I have figured it out. This is probably caused by the fact that my home folder is encrypted. I'm still not sure if this should be default behaviour.

---

### Post by grahammechanical on 2012-05-17
It is possible to put an image in the Pictures folder, which is of course in the Home folder and then tell the Appearance utility to look in the Pictures folder for the background wallpaper. Perhaps this is what the other user has done.

In the Appearance utility there is a drop-down menu just above the panel where the background images are shown for selection. That menu says Wallpapers, Pictures Folder, Colours and Gradients.

Regards.

---

### Post by mcduck on 2012-05-18
> **ckop64 said:**
> I think I have figured it out. This is probably caused by the fact that my home folder is encrypted. I'm still not sure if this should be default behaviour.

It pretty much *has* to be the default behaviour, there really is no other possible way, if your home is encrypted the LightDM will not be able to access the background image as the encryption is only opened *after* you have logged in.

Same goes for unencrypted home directories when the read permission is removed from other users than the owner. LightDM runs as a different user and will not be able to access the picture. (such permission issue could be worked arounf by creating a symlink from the iamge file into /usr/share/backgrounds, but that of course doesn't work with encrypted home directory.)

---

### Post by Charlotte18 on 2012-05-18
Are you trying to get this to work for multiple users or only for one user?

---

### Post by aarons6 on 2013-01-31
i have this same problem but different.. 
the greeter works with every background except the one i want.


it used to work with the one then one time i restarted and the greeter was purple with no background.

ive tried to purge it, reinstall it, reboot 1000x.

if i change to a different background, even ones in pictures folder it works.. any ideas? 
its gotta be some config in my home folder?

---

### Post by grahammechanical on 2013-01-31
@aarons6

It is better to post a new thread for your problem that open an old thread. Thhis is true even if we have the same problem. But you do not have the same problem. Do you?

Post a new thread and tell us if this particular background image that you are having problems with is one of the official background images or if it is an image that you want to use as a background image.

The person who started this thread wanted a background image to become the unity-greeter image. Is this what you want to happen?

Regards.

---


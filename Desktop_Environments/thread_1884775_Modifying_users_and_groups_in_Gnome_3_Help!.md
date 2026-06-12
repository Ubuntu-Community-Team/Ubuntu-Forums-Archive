---
title: "Modifying users and groups in Gnome 3??? Help!"
date: 2011-11-21
forum: Desktop Environments
---

### Post by travlemon on 2011-11-21
Hello,

I have Ubuntu 11.10 installed on my system.  I was displeased with Unity, so I got rid of it and I am happy with Gnome 3.  I like where the desktops are going with the tablet-ish styled interfaces, and I just happen to like Gnome 3 much better than Unity.  

ANYWAY, I have a problem with Gnome 3 and I can't seem to find anything on Google.  I simply want to add my username to the vboxusers group for VirtualBox, but when I go to "User Accounts in the System Settings application, I'm only able to change minor things like the user's name, password, user type, etc. 

I've already click the "Unlock" button to make sure I'm using it with administrative privileges, but I can't find out how to simply see the groups and add/remove myself to and from groups.

In Gnome 2, I simply when to System>Administration>Users and Groups and it was all available there.  I know I can add myself via the command line, but it's really bugging me and I'd like to know where it would be located. 

If anyone knows, please let me know.  It would it be much appreciated!  Thanks in advance.

---

### Post by Copper Bezel on 2011-11-22
You should still be able to use the manual process described [_here_]("http://www.webupd8.org/2011/02/get-your-usb-drives-to-work-with.html"). The option doesn't exist in the GUI, to my knowledge, but the file seems to use the same syntax.

---

### Post by travlemon on 2011-11-22
> **Copper Bezel said:**
> You should still be able to use the manual process described [_here_]("http://www.webupd8.org/2011/02/get-your-usb-drives-to-work-with.html"). The option doesn't exist in the GUI, to my knowledge, but the file seems to use the same syntax.

Thanks very much! I had a feeling the answer might be that it's not in the GUI.  Hopefully it gets added later on.  I like the direction of Gnome 3 though.  Thanks again!

---

### Post by de Bacon on 2011-11-22
I noticed that GUI interface to be inadequate and cumbersome. I feel the use of scroll down menus for that type thing is the major problem, especially for those who are not real fluent in user accounts, their possibilities etc.  A full screen of options with check boxes is much easier to verify than things that disappear past the roller window.  Maybe it will be upgraded to a more user friendly interface sometime, the sooner the quicker.   

I too had to go to Gnome, finding Unity quite like stepping into an alien country with language barriers.  We may be forced to adapt that way due to trends though :(

---

### Post by Copper Bezel on 2011-11-22
Well, it's a Gnome 3 thing; that means it applies whether you're using Unity or Gnome Shell as the shell. (Or Fallback, for that matter.)

[QUOTE=travlemon]Hopefully it gets added later on. I like the direction of Gnome 3 though.[/QUOTE]
Yeah, I'm torn. I guess the best way to put it is that I appreciate how much cleaner the settings windows look now that they don't have any features in. = ) It seems like doing deep tweaks in Gnome has always meant digging through text files and gconf anyway, and that's only exaggerated with Gnome 3, but I'm not going to say that it hasn't caused me some hassles thus far.

If that method worked, be sure to mark the thread as Solved in the Thread Tools at the upper right. Thanks! = )

---

### Post by travlemon on 2011-11-22
> **Copper Bezel said:**
> If that method worked, be sure to mark the thread as Solved in the Thread Tools at the upper right. Thanks! = )


It worked just fine for me.  Thanks a lot!!  I will mark this thread as solved after I submit this reply!

On a side note, I must say it it would be worth it to check out Mint 12, they tweaked Gnome 3 in the best interest of the users.  Perhaps they'll make all the right improvements!  The Mint 12 RC1 is out now.

---

### Post by Copper Bezel on 2011-11-22
I don't think Mint's tweaks go very deep, though. It's the same issue as with Unity - a different UI over the same applications, including the settings managers - except in that Mint is using Gnome Shell with extensions instead of an alternate window manager and shell like the Compiz-Unity set. 

They're also giving the option of using the old Gnome 2 stack, of course, but that doesn't directly affect the Gnome 3 experience.

Should be noted, too, that everything is theoretically written to be used by users - Mint is preferring a certain subset of users, as are the Ubuntu folks and the Gnome folks and so on.

---

### Post by Bobhuber on 2011-11-22
> **travlemon said:**
> Hello,

I have Ubuntu 11.10 installed on my system.  I was displeased with Unity, so I got rid of it and I am happy with Gnome 3.  I like where the desktops are going with the tablet-ish styled interfaces, and I just happen to like Gnome 3 much better than Unity.  

ANYWAY, I have a problem with Gnome 3 and I can't seem to find anything on Google.  I simply want to add my username to the vboxusers group for VirtualBox, but when I go to "User Accounts in the System Settings application, I'm only able to change minor things like the user's name, password, user type, etc. 

I've already click the "Unlock" button to make sure I'm using it with administrative privileges, but I can't find out how to simply see the groups and add/remove myself to and from groups.

In Gnome 2, I simply when to System>Administration>Users and Groups and it was all available there.  I know I can add myself via the command line, but it's really bugging me and I'd like to know where it would be located. 

If anyone knows, please let me know.  It would it be much appreciated!  Thanks in advance.

I know this is closed but you can add the gnome-system-tools package  thru synaptic and you will have a full blown GUI with administrative privileges for users and groups. users-admin

---

### Post by travlemon on 2011-11-22
> **Bobhuber said:**
> I know this is closed but you can add the gnome-system-tools package  thru synaptic and you will have a full blown GUI with administrative privileges for users and groups. users-admin

Oh wow, thank you!  This is the exact utility I was looking for!  I probably should have asked about this being available/compatible with Gnome 3...but I checked Synaptic and was unable to find it, and assumed it would not be available.

Thanks so much!

---


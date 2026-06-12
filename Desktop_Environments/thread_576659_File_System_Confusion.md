---
title: "File System Confusion"
date: 2007-10-15
forum: Desktop Environments
---

### Post by alpinegroove on 2007-10-15
I am confused about the location of my Desktop. I realize that my confusion probably has to do with the fact that when Installed Ubuntu, I designated the computer's name as Desktop.

 When I go to File System, and then open the "home" folder, I see another folder, called "desktop" and having a little stylized home icon on it.
I open this folder and get a list of folders including Documents, Music, Public, etc. 
One of the folders is called "desktop" and it has an icon of a desktop above it, that is, an brown square icon with brown triangles on its corners. 

What is the difference between the two "desktops"?
How do I change the computer name in order to avoid this duplicity?

When I download a file from Firefox, it saves it automatically under desktop (with the little house) and not on the actually desktop that I am seeing as a desktop (with the triangles). How do I change that?


Thanks!

---

### Post by TeaSwigger on 2007-10-16
Hello, you'd probably get more help for this in the "Absolute Beginners" forum but I'll try to help.

> **alpinegroove said:**
> I am confused about the location of my Desktop. I realize that my confusion probably has to do with the fact that when Installed Ubuntu, I designated the computer's name as Desktop.

 When I go to File System, and then open the "home" folder, I see another folder, called "desktop" and having a little stylized home icon on it.
I open this folder and get a list of folders including Documents, Music, Public, etc. 
One of the folders is called "desktop" and it has an icon of a desktop above it, that is, an brown square icon with brown triangles on its corners. 

What is the difference between the two "desktops"?
How do I change the computer name in order to avoid this duplicity?

When I download a file from Firefox, it saves it automatically under desktop (with the little house) and not on the actually desktop that I am seeing as a desktop (with the triangles). How do I change that?


Thanks!

It sounds to me like you mean that you named your user name Desktop? One way you can change that is making a new user with a new name. Be sure to make this new user part of the "sudo" group. Test a sudo command as the new user. Save your files if any by copying them to your new user's home folder and change their user and group permissions to your name. If everything's cool, you can delete the old user "Desktop."

File System:

/

Directory in which "Home folders" are located:

/home/

Thus:

/home/desktop

is your "Home folder" yeah? That will have the house icon. In it should be your music folders etc, etc. Also in there is the "desktop" with a literal desktop icon (image of a desk's top with a writing pad etc) - the desktop is actually a folder in your home folder, so it's:

/home/desktop/desktop

If you created a new user named matterhorn, that'd go:

/home/matterhorn

for matterhorn's home folder and

/home/matterhorn/desktop 

would be the desktop for the user matterhorn.

Is that any clearer?

Perhaps Firefox is set up by default to download to your home folder. That's /home/desktop. Anyway, to have it download to /home/desktop/desktop or anywhere you please, go to the Edit > Preferences menu. Under the "main" category you'll find the "downloads" section where you can change it's behavior to suit you. :)

---


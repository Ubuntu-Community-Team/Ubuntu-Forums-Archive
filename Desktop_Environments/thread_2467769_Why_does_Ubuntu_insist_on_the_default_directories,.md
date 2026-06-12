---
title: "Why does Ubuntu insist on the default directories, and what is the purpose of Desktop"
date: 2021-10-07
forum: Desktop Environments
---

### Post by cyberhiker001 on 2021-10-07
I think it has been about ten years now that Ubuntu has implemented the default directories - why?!?!?!

Documents
Downloads
Music
Pictures
Public
Templates
Videos

It would seem that the list is a good suggestion for novice organization of files, but once a user becomes experienced, the list tends to have some structural problems. I never use "Public," for what it is seemingly designated for. In any event there still does not seem to be an easy way to prevent Ubuntu from recreating the directories upon logging into the account. Why??? The dirs-dirs file still does not explain how to redirect the default to a subdirectory, which is what I do with Music. For me "Music" is a subdirectory of the Audio directory - where else am I supposed to put my audio editing files. And why wouldn't I make Music a subdirectory of Audio???

And then, why wouldn't Documents be a subdirectory of Desktop??? 

Which leads to the Desktop problem - it would seem that the Desktop is a place for the visual sorting of files, but the Desktop icon system is always irregular - it is never stable. It is like it always gets messed up upon logging in.

You have all these fancy window systems that are supposed to make organizing open applications convenient for different ways of thinking, but the Desktop feature remains "old." 

Thank you for entertaining my grievances.

---

### Post by ActionParsnip on 2021-10-07
Documents isn't a subdirectort of Desktop. This is nonstandard so you made this yourself. By default $HOME/Desktop and $HOME/Documents are separate.
The folders (as far as I know) are not created at each and every login but I'm happy to be wrong here. You can use
```

cat $HOME/.config/user-dirs.dirs

```
To see the current configuration for the user folders.
You can use something like the below:
```

mkdir $HOME/Downloads/Music
xdg-user-dirs-update --set MUSIC "$HOME/Downloads/Music"

```
and move things around as you like.

---

### Post by GhX6GZMB on 2021-10-07
I'm failing to see the problem here. The UNIX/POSIX/Linux directory structure is well defined and standardised.
One basic directory is /home where every user is free to do whatever he/she wants in their private subdirectory (aka $HOME or ~)

Every user has an own desktop, and thus a $HOME/Desktop directory which defines the icons in the Application Menu and on the Desktop.

What's wrong with this?

---

### Post by QIII on 2021-10-07
What makes you believe is should have changed, or the fact that it hasn't indicates that something is wrong?

You are free to create your own directories as you choose and have them be wherever you want.

Don't, however, expect an OS that expects compliance with a well-established and standardized file structure to work perfectly if you get too carried away.

---


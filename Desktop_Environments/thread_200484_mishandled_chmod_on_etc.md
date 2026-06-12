---
title: "mishandled chmod on /etc"
date: 2006-06-20
forum: Desktop Environments
---

### Post by Jorguntu on 2006-06-20
OK, this must be the biggest screw up a typo has caused me, ever. Please help!

Here's the deal. I needed to append something in the /etc/profile file so instead of playing safe like I should have I just went ahed and changed the permissions of /etc from 755 to 777 and that of /etc/profile from 644 to 666. I opened up /etc/profile and added what I had to add, saved and closed it. Now, when I wanted to revert the permission back to its original form, something horrible happend. Instead of setting /etc 's permission back to 755 I set it to 644 thus eliminating all execute permissions.

These are the repurcussions I noticed:
[LIST]
[*]File owner and file group that previously had root set to them now have '0' set to them
[*]File owner and file group that previously had my user account set to them now have '0000' set to them
[*]When trying to view permission of files located in /etc, I get "The permissions of "filename" could not be determined"
[*]I have not checked what are the file group and owners of other files that used to have different owners and groups then my account or that of root. But I'm sure it's also screwed up.
[/LIST]

Because permissions have been reset for /etc, I cant execute crutial applications like the Terminal. Even if I could, I wouldn't be able to execute sudu command to fix the permissions because file ownership and group of sudoer has alse been set to '0'.

I can't open my files either because I don't have access to a text editor. At least I think that's why.

I have a lot of unbacked code for the project I'm working on so it would really  suck If I lost everything.

I have not restarted Ubuntu for fear of of being unable to log back in and losing data.

Is there a way to reset all of this back to the way it was? Through Ubuntu Safe Mode? What happens if I restart?

I have the 5.05 distrubution, by the way. I was procrastinating on the update.

Any help will be much appreciated.  Thanks!

---

### Post by givré on 2006-06-20
I think the best think to do is restore pemission via a live CD. Hope it helps, i defintly wouldn't like to be in your position :cool:

---


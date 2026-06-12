---
title: "So I just corrupted my home partition..."
date: 2009-05-22
forum: General Help
---

### Post by MJBoa on 2009-05-22
What I want to do is add a user so that I can skip reinstalling ubuntu. I know the command for adding a user, what I want to know is, will this user still function normally if I add it through the command line? What are the default groups that Ubuntu adds the first user to so I can use sudo and have normal privileges? Do I need to do anything else?

---

### Post by baseface on 2009-05-22
what do u mean by "corrupted"?
yes adding a user via the shell will do the same thing as adding one thru whatever gui is there.

---

### Post by taurus on 2009-05-22
If you plan to create a new user for yourself, at least make sure the new user belongs to group admin or you won't be able to modify (sudo/gksudo) anything outside of your $HOME.

---

### Post by MJBoa on 2009-05-22
Well I was resizing the partition with gparted and canceled during what I thought was a test run or while it was just reading. That's a bad idea it turns out and I didn't have that much vital data on there to care enough to try to recover it. 
New question though, how do I simply change the /home location of a user because I just realized that my user still exists because that info is all on / and that's a different partition, it's just that there's no location for home. If I just create a folder 'mike' on /home will Ubuntu create everything it needs when I next login?

---


---
title: "Rebuilding evolution folders?"
date: 2008-12-07
forum: General Help
---

### Post by sandman3838 on 2008-12-07
Hello ):p

i just reinstalled ubuntu, i guess its also an upgrade from 804 to 810.
Anyway i read somewhere that all you needed to do was to save the "home" folder.  This i did but not before i un-hide the home folder before coping it over to another drive.

Well the reinstall went fine and i didn't copy the entire home folder back.  All i copied over was my material.  As for the hidden folders all i moved back was the themes and icons.  Right now everything is back and running just fine but quicker.  The reinstall really helped!

However, naturally it's the email program evolution that is giving me the fits!
It's always the email!  Even in windows?  I know i know i should have used evolutions backup program.

Anyway the files are all there in the /home/.evolution
but for some reason only some of the folders, archive folders, are showing up within evolutions folder tree.

I just did a removal of evolution from synaptic manager, deleted out the files and folders in the /home/.evolution.  Next i moved in my saved evolution folders, lastly i re-installed evolution through synaptic manager thinking it would pick up the folders?  It didn't just the same problem with the same folders?

Somewhere there has to be a log or directory that is preventing the files from showing in the evolution file tree?

Oh!  I should mention that through this whole process i has careful in using the ctrl+h keys to reveal al the files, to make sure nothing was left behind of missed?

Any ideas???

Thank you all!

---

### Post by dcstar on 2008-12-07
> **sandman3838 said:**
> 
.........
Anyway the files are all there in the /home/.evolution
but for some reason only some of the folders, archive folders, are showing up within evolutions folder tree.

I just did a removal of evolution from synaptic manager, deleted out the files and folders in the /home/.evolution.
.........

Evolution files do not exist in "/home/.evolution", they exist in "/home/your-user-name/.evolution" and need the same owner credentials as all other files in your home directory.

---

### Post by sandman3838 on 2008-12-07
Sorry you right i did mean to say

home/username/.evolution

still, i do have that backup of the original folders off on the other drive.  Any suggestions on how to rebuild or change the ownership over?

Note i have had some other issues here and since this set-up is so new i'm seriously thinking about doing a re-install of ubuntu.

Thanks for your help!

---

### Post by bp1509 on 2008-12-07
d

---

### Post by bonfire89 on 2009-01-18
oh, I ran into the same problem.

I copied the .evolution folder with the intention of just throwing it back into my new home directory.

I have run the ownership command above, but still... when I try and run evolution it acts like it is being run for the first time.




However!!!!!!!!!!!! I went to the website up above, and eventhough the final two commands didn't work I some how got it to work with the other ones. Of course appending the first couple that creates the archive to deal with my back up!


Thanks!

Saves me from setting up my several imap email accounts

---

### Post by sandman3838 on 2009-02-01
After playing afoun with this issue I read an interesting review on Thunderbird.

So I swithched to it!  Why...

It is available in both Winxp and Ubuntu!
Using Thunderbird Winxp I moved my folder location to anohter HD.  Next I let Thunderbird do a import from my Winxp Outlook Email.
Finally, I setup my Thunderbird Email in Ubuntu and pionted my folder location to the same Winxp folders.

i can now access the same Email on both OS's.

So far I havn't had any issues?

---


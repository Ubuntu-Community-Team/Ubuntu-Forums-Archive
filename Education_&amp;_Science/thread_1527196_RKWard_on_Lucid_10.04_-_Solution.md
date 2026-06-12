---
title: "RKWard on Lucid 10.04 - Solution"
date: 2010-07-09
forum: Education &amp; Science
---

### Post by mech14 on 2010-07-09
I'm running an Ubuntu 10.04 VM so I can use Kile, the mother of LaTeX editors.

For my stats, I rely on R, usually on OSX, but wanted something working in Ubuntu as I use Sweave a lot and often have to jump into R.


I installed R after updating the repo to latest one via suggestions on [http://www.keittlab.org/node/158](http://www.keittlab.org/node/158) 

Then I wanted to install a good GUI and RKWard was recommended online. Seems it is actively maintained for Ubuntu as well.

When I used Synaptic to install it, it wouldn't work at all and spat out multiple permission errors. All of them had to do with .kde folder not being under my ownership.

I found that I could run RKWard from terminal by 'sudo rkward', but this is a hassle, so below is a solution until they fix this up.

SOLUTION:

1. open a terminal window; type in 'gksudo nautilus' and enter your password
2. navigate back from 'root', and go to 'home', then 'yourusername' folder, then press Ctrl-h to unhide hidden folders/files
3. right-click on '.kde' and select Properties
4. under Permissions, change the Owner to 'yourusername'; Folder Access should be 'Create and delete files'
5. Group can stay as 'root', but change the other 2 options for Folder Access to 'Create and delete files'; Lastly, click on 'Apply Permissions to Enclosed Files'
6. make sure to RESTART the system
7. Now RKWard will appear in Applications->Science and should be running without crashes.

This fixed it for me. Let me know if there is an easier way of doing all of this. I'm not very savvy w/ linux.

---

### Post by mech14 on 2010-07-21
I discovered that 'click on 'Apply Permissions to Enclosed Files'' does not work in Ubuntu and I had to do this in terminal.  As a bonus, this fixes Kile permission errors as well.  Not sure why, but the KDE installation via synaptic does not allow the user the ability to read/write to the necessary folders. This problem seems to affect the /home/USER/.kde directory only because fixing the permissions errors of all folders/files fixes all issues.  Here is what I did:     

1) fix ownership: sudo chown -hR root:users /home/USERNAME/.kde    

2) fix permissions: sudo chmod -R a+rwx /home/USERNAME/.kde 
(replace USERNAME with your user name, of course, enter your password).     


Hope this helps others in a similar situation.     

NB: I'm running this in a virtual machine, so I'm not sure how a natively installed Ubuntu 10.04 reacts to KDE applications.  Cheers

---


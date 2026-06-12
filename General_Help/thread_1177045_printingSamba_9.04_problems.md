---
title: "printing/Samba 9.04 problems"
date: 2009-06-03
forum: General Help
---

### Post by Themotorman on 2009-06-03
Printing problem 9.04 now worse..After I upgraded to 9.04 I could no longer print to my winbox based printer via a lAN. I tried all the ideas you nice people have offered , nothing worked. I decided to try reinstalling SAMBA..
Now I have samba installed the choice to go to System>Admin>Printing has vanished and I have Samba in its place. However clicking on Samba doesn't seem to help with printing. How do I get "printing" back? I miss it even though it has a bug... 
Thank you Ubuntu is otherwise a fantastic system.

---

### Post by twrock on 2009-06-06
Sorry, I don't know how to get printing back, other than if all else fails, you can try a full system reinstall. I know that's a hassle, but it's a lot more easily done than a reinstall of MS Windows.

After that, maybe my post below will be useful to get network printing to work.
I got the ideas from this post:
[http://ubuntuforums.org/showpost.php?p=7214797&postcount=6](http://ubuntuforums.org/showpost.php?p=7214797&postcount=6)

---

### Post by twrock on 2009-06-06
This is a follow up, for my own reference if no one else finds it useful. :-)

Click Main Menu>System>Administration>Printing
Click New>Network Printer>Windows Printer via SAMBA
Hit the "Browse" button. "SMB Browser" box pops up. Note the names under the headings labeled Share and Comment. (So in my case, under "Share" was MSHOME and under "Comment" was DESKTOP1.)
Cancel out of the "SMB Browser" window. Click in the entry box beside smb:// and enter those name in this form: ShareName/CommentName/
Click "Browse" again. This time the list should be populated in the "SMB Browser" popup box (after a short wait) with the names of your shared printers. Choose the one you want and proceed with the installation.

Hope that helps someone else.

---

### Post by mafaldaspeaks on 2009-06-10
> **twrock said:**
> This is a follow up, for my own reference if no one else finds it useful. :-)

Click Main Menu>System>Administration>Printing
Click New>Network Printer>Windows Printer via SAMBA
Hit the "Browse" button. "SMB Browser" box pops up. Note the names under the headings labeled Share and Comment. (So in my case, under "Share" was MSHOME and under "Comment" was DESKTOP1.)
Cancel out of the "SMB Browser" window. Click in the entry box beside smb:// and enter those name in this form: ShareName/CommentName/
Click "Browse" again. This time the list should be populated in the "SMB Browser" popup box (after a short wait) with the names of your shared printers. Choose the one you want and proceed with the installation.

Hope that helps someone else.

Would you know how to do this in kubuntu 8.04 which I'm using with my laptop? I need to use the HP PSC 1400 on my windows network.

I've started using samba but it can't seem to "find" the printer I mentioned above.

---

### Post by twrock on 2009-06-11
Sorry, but I have no idea of what the differences are in Kubuntu. Interestingly, I didn't have this kinda of problem with Ubuntu 8.04 or 8.10. It showed up with 9.04. So I'm not sure why you are getting it with 8.04.

---


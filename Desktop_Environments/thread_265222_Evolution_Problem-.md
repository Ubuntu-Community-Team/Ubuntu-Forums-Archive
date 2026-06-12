---
title: "Evolution Problem-"
date: 2006-09-25
forum: Desktop Environments
---

### Post by itconsultant1996 on 2006-09-25
I love the evolution email client, but I just had a bizarre problem with it.   I had emailed several photos, and cc'd myself on it,  I mistyped my sister's email address, so it bounced back to me from yahoo saying so.  The problem is that when yahoo does this, it sends the entire email back, and apparently strips off the encoding that allows evolution to recognize the headers that they are photo attachments. so all I get is the typical tcpip headers and text, and then the rest of the email is the code for the photos.  No big deal right?  Well, evolution hangs up the entire pc trying to decipher what the heck is going on there.  It gets so bad that the entire pc hangs until I can get a click in that kills evolution, or I reboot.  

Now the problem is that when I restart evolution, it tries to display the text of the email at the top of it's inbox, which happens to be this email from yahoo mentioned earlier.  How can I interrupt the startup of evolution and delete this email, or how can I get evolution to not display the text upon startup?  Problem is that once it starts, it starts to last config, and this is the point that it's hung up on....

Apparently I'm going to need to uninstall evolution and reinstall it, so if anyone has any suggestions on how to do so and archive the emails in it without starting the program up (which freezes the entire pc due to this problem, of course).  

Help!

---

### Post by Sarisar on 2006-09-25
The emails should be stored in ~/.evolution so you may be able to edit those... although I don't know the specifics.  You can go in there into /mail/local and see an 'inbox' file that does have stuff from your inbox.

* Warning * If you're gonna play with these files back them up first and don't blame me if you break it please :)

---

### Post by itconsultant1996 on 2006-09-25
Hmmm....good idea.  I tried uninstalling Evolution, but Ubuntu won't allow it to be uninstalled.  How the heck do you uninstall Evolution?  Arrrrrggghh!!!!  

I hate bugs....this is one that Novell/Ximian should have caught...

---

### Post by wael_hossam on 2007-08-15
Hi there,
To unistall evolution you need to go to the Synaptic Manager under system / Adminstration menu... :)
But to blow your smile, evolution won't forget that it should always start by that crash email even after you re-install it!!!
I have the same problem here.
Good luck with open source, i think I am going back to Outlook :(
Wael

---


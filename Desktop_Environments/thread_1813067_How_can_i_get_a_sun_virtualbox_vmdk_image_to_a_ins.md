---
title: "How can i get a sun virtualbox vmdk image to a installation iso"
date: 2011-07-27
forum: Desktop Environments
---

### Post by PaulNL on 2011-07-27
Hello all,

I have a working system in Virtualbox, now i wan´t to transfer the installation so i can boot my machine with it.

I have already tested remastersys but the iso gives errors. Does some one know a way to transfer a virtalbox image to a iso installation file =

Paul

---

### Post by varunendra on 2011-07-27
I'm sure there must be a 'standard way' to transfer linux installations, but I'm also sure it must be a complex process, that's why remastersys is so popular. Sorry for such a no-answer reply, but I think troubleshooting remastersys errors may be easier.

Can you post the errors it gives you?

Alternatively, you may try creating image of your installation using clonezilla, then restore it on the desired machine. It may involve some minor glitches, maybe some post-restoration steps, but should do what you want.

---

### Post by PaulNL on 2011-07-28
My problem when i make a iso with remastersys is that when i want to start te live cd on Sun Virtualbox i get the massage "mounting aufs on /root failed: No such device"

What can i do about that ??
i used the command "sudo remastersys backup"

Paul

---

### Post by varunendra on 2011-07-28
Having no idea about that error message at the moment, I'd suggest to try remastersys GUI. Maybe the commandline needs some extra parameters to create a compatible iso. I've been using it (GUI) for quite some time and all my virtual machines (VBox or VMware) boot from those ISOs without problems.

---

### Post by PaulNL on 2011-07-28
The probel is that i work with a minimal installation no desktop just the things what it needs to be a server.

---

### Post by varunendra on 2011-07-28
What about trying out clonezilla thing? And did you ever tried that remastersys command successfully before? Maybe going through its man page could clear up something.

---

### Post by PaulNL on 2011-07-28
CloneZilla did the jop Thanks

---

### Post by varunendra on 2011-07-29
> **PaulNL said:**
> CloneZilla did the jop Thanks
Good to hear that.

I'll try out remastersys commandline myself and post the results back here, but can't say when. For now, I think you should mark this thread as [solved].

---

### Post by PaulNL on 2011-07-29
The only problem is that now it works on a new computer but he don't have a network card installed and does someone know how to do hat without a networkconnection. ??

---

### Post by varunendra on 2011-07-29
> **PaulNL said:**
> does someone know **how to do hat** without a networkconnection. ??
..not clear what you want to say.. I assume your 'hat' means 'that', now what is that 'that'? And please try to use complete words in forums because understanding a problem becomes more difficult if we have difficulty in understanding the language first.:)

Please explain clearly what is it that you want to do 'without' network connection.

---

### Post by PaulNL on 2011-07-30
Sorry

Now i have the virtualbox ubuntu working on a normal pc but i can't get the networkcard to work.

So how do i install it ?? can i use the files from a live cd ?? 

I have a onboard Itel networkcard.

---

### Post by varunendra on 2011-07-30
> **PaulNL said:**
> Sorry

Now i have the virtualbox ubuntu working on a normal pc but i can't get the networkcard to work.

So how do i install it ?? can i use the files from a live cd ?? 

I have a onboard Itel networkcard.
That is a different problem which may require quite a number of stepwise instructions to follow. So post this problem as a new thread and mark this one as [solved] (follow the 'see how' in my signature).

As your current problem does not correspond to the title of this thread, it is less likely that right people, who could help with that matter, would look at this one. That's why it is recommended to put different problems in different threads.

So start with searching the forums to see if a solution for your problem already exists. If not, then start a new thread of your own under 'networking and wireless' section of the forum. You may then post here a link to that thread so that we can follow it.

---


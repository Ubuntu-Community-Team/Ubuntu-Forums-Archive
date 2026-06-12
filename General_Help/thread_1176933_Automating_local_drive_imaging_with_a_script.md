---
title: "Automating local drive imaging with a script??"
date: 2009-06-02
forum: General Help
---

### Post by jm8254og on 2009-06-02
Hey everyone,

I am attempting the following:

I need to automate drive imaging for end users in an organization.  My goal is to create a boot disk that runs a script on startup and assesses the mount point of the local drive and then an external usb drive and then makes a raw image of the drive.  My thoughts were to just use a bash or perl script that determines the mount points and passes them as parameters to the dd command.  I also want to generate a basic report in the end based on some user input.  

My questions are:  

Is that a good idea?

Is there a much easier way I am overlooking?

If not anyone know a good method of determining mount points and passing them correctly as source and destination parameters?  I have written/modified a similar script in vbscript that would pass a usb drive letter as the parameter and that was not too difficult.  I just am not finding an easy solution for perl.  Oh and I am not hung up on perl I just have used it but I am open to whatever.

Basically its for doing a forensics analysis on the image of drives that are on computers that are located off-site.  Currently the solution is a Ghost boot disk with some batch files that run but it will not work with sata drives.  It gives the user prompts and is very basic.  I didn't want to go that route and thought my idea would be more scalable in the future.  Any thoughts?

I know there are other solutions such as remote imaging over ssh and such but I am not sure I will be able to implement that in the time I have based on the infrastructure in place. 


I didn't know any good script forums and I use ubuntu mostly so thought I would start here.  Please move this or let me know where to post.


Thank you so much for any input.

---

### Post by munky99999 on 2009-06-02
Quite confident that you could write a bootable rsync-echo script for that purpose.

Google something like differential rsync script. It'll be fairly long so posting in this a post will be yawn :(

---

### Post by jm8254og on 2009-06-02
Will defiantly check it out.  Thank you.  I don't mind searching at all and always do before I post.  You gave me some new key words to try and hunt it down with.  Thanks again!

---


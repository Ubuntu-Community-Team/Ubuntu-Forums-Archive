---
title: "Evolution lost mail"
date: 2009-04-27
forum: General Help
---

### Post by hemmi7 on 2009-04-27
Hello 

Hello I Use ubuntu with evolution 2.24.3 

Now evolution lost a mail in the sent items. 

Story: 3 days ago I sent a mail. (some unformatted text, 2 atttachements totally 3MB.)
After I sent it, it was in my sent mails, Because I printed it some minutes after sending it. (to make some remarks on it)

When I today tried to view this Mail it has somehow gone. 
In the list of the sent mails the mail is Present with adress, subject, and the sign that there is at least oone  attachement in the mail. 
But if I click it. there is nothing,  The Window that opens is completely empty. No Header informations, no body text and of course also no attachements.

What happened to this mail?
Can I undo it?   How?

I use evoultion with a pop server. And somehow all sent mails are downoaded and stored locally despite ive set the option to let the mails on the server.    (Ok I guess thats another question, but why not solve two problems at once :-) )


Gr Hemmi7

---

### Post by hemmi7 on 2009-04-28
Hello Again 

By now I lost two more mails.  but I'm also getting closer to the Problem:

When I switch from the sent Folder to another folder e.g. inbox. Then I get in the bottom line an error mesage:

German Version Error: Im Ordner "Sent" wird gespeicher.

Transated about:  Error: Thr folder "sent" is beeing saved.

 
My HD has by far enough space left.      


But I hope this helps. 

Gr HW

---

### Post by hemmi7 on 2009-04-28
OK  I solved the Problem

The correct english translation of the before mentioned error is:  Error while Storing folder 'Sent'.

And in the Net I found the following solution. By now the Sent-ev-summary is called sent.{something}. 
so I deleted all these sent.ibex  and sent.index files.   But I let the sent file there.

By< the way: All the mails that I thought were  lost came back, when the index was freshely built. 



                                  **Re: Error when starting Evolution  (Solution for inbox, but works also for sent.)**             
                                                                Looks like it is telling you simply that your inbox file doesn't match up with your inbox_summary file.

Go to the Places menu>Home Folder and open Nautilus.

Click on View and Show Hidden Files.

Navigate your way to the .evolution/mail/local folder. There you'll see several files concerning your inbox. One called Inbox, another called Inbox-ev-summary.

Copy (not move) your .evolution folder to another location for backup purposes. You could just backup the local directory you were just viewing, but myself, I would feel safer having the whole directory backed up. Then it is a simple matter of just copying the safed folder back into it's proper place.

Next rename the Inbox-ev-summary folder to something like Old-Inbox-ev-summary and then restart Evolution. See if this solves your problem. I experimented with my own Evolution and this method just recreated a fresh Inbox-ev-summary file for me.



Thank you for the Big help  :lolflag:

                         Gr Hemmi7

---


---
title: "Prevent CUPS from spooling/caching print jobs"
date: 2009-04-16
forum: General Help
---

### Post by er4z0r on 2009-04-16
Hi there,

I am not sure if this is the right forum, but I could not find any better.

Setup:
We have a small computer lab with tweleve computers, that allow 
to surf, check their e-mail and print their scripts.
For printing we have a server running cups, that advertises the printer among the client machines. 

Problem:
Trouble starts, when the printer is for some reason disconnected or out of order. Because in this circumstance the printjobs started on a client-machine by a student just gets queued locally in the spool-directory until the printer is available again. So the users so that their document is not being printed and they resubmit it. So it gets queued locally again. 

Effect:
Once the printer is started again. All the clients start firing the contents of their spool to the printserver, which starts printing stuff, that was queued by students maybe a few hours ago and is of course of no interest for the users, which want to print now that the printer works again.

Final question:
How can I prevent my client computers from just queueing the jobs.
I would rather like the clients to simply show the user an error and
throw the job away.

Please help us, so our users won't blame linux for their printing problems when they sould be blaming the ignorant admin instead ;-)

---

### Post by StuartN on 2009-04-16
I am not sure if this will work for you - I use a simple wireless USB printer server, and get resubmitted jobs when the wireless link is lost.

I went into System->Printing and selected the wireless printer, then in the Policies tab, set Error Policy to "abort job" instead of the default "retry job". Now there is a warning that the printer is unavailable if anyone tries to print when the wireless is down. The user can cancel the job or leave it queued, but certainly know it did not print.

---


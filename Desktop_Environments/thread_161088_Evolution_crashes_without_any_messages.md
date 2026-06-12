---
title: "Evolution crashes without any messages"
date: 2006-04-16
forum: Desktop Environments
---

### Post by gerases on 2006-04-16
Evolution used to work just fine but all of a sudden I couldn't start it again. I tried moving the .evolution folder out of the way and even the evolution folder under .gconf. I see no messages when the crash occurs. Basically what happens is I click on the evolution icon, the cursor changes to "busy" and then changes back to the regular cursor -- all of that probably within 4-6 seconds. I upgraded from breezy to dapper recently but it worked fine for a while. 

I just switched to another user and evolution started just fine there.

Any ideas?

==========================================

Follow-up:

The problem is solved. I did ps ax | grep evolution and found a whole bunch of evolution processes running. I killed all of them and restarted evolution. Evolution brought up the initial setup screen. I filled out the info and it finally started with all the messages and folders intact. Don't know what caused it all but it's working.

---


---
title: "Modem Busy, And Other Trinkets"
date: 2005-07-27
forum: Desktop Environments
---

### Post by [TCK] on 2005-07-27
Greetings.

I've recently installed Kubuntu, and the first thing I figure I should sort out is the internet connection, with KPPP.  

1) Opening that gives me a message about something not being found or not having access (I'm pretty sure this isn't connected to the main problem I'm having).  I've checked the documentation detailing how to remedy this which involves giving a command line.  This probably shows how inexperienced I am at anything other than Windows in general, but I'm really not sure where to enter these lines.

EDIT: I gather this is a case of using Konsole.  These are the lines I have to enter:

% su root
# chown root:root KDEDIR/bin/something
# chmod KDEDIR/bin/something
# exit

I tried entering su root but was greeted with a password entry dialogue.  Is there a universal password for the root?  And are the %, $ and # particularly important?

2) The main problem.  I've put in all the details about the modem/connections and what have you, however, when trying to connect through the modem, I'm told that it is busy.  I see no reason why it should be busy.  Any ideas why, and how to solve this?

3) As an aside, I noticed when installing Kubuntu that there were a few commands when booting that gave a "fail" response.  Should this be something to worry about in the future, or is this the way with pretty much all Linux systems.

Thanks.

---


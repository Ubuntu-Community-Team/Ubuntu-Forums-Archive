---
title: "set process user in init.d"
date: 2009-03-10
forum: General Help
---

### Post by pab10 on 2009-03-10
how to I set the user to something other than root for a service I want to start in init.d

I have set up a shoutcast script and run update-rc.d

when restart server the app has root privelages even though its run from user directory

I just did chown 6751 on the sc_serv program which exists in a user directory and restarted the server and it seems to be running as user that owns the file (user level account) 

Is that right? (thats what I think I want...)

do I just need to set the SUID bit or do I need to set both SUID and GUID

does this give slightly more security? as if the process is compromised it now only has user level access?

---

### Post by kryptikos on 2009-03-10
> **pab10 said:**
> how to I set the user to something other than root for a service I want to start in init.d

I have set up a shoutcast script and run update-rc.d

when restart server the app has root privelages even though its run from user directory

I just did chown 6751 on the sc_serv program which exists in a user directory and restarted the server and it seems to be running as user that owns the file (user level account) 

Is that right? (thats what I think I want...)

do I just need to set the SUID bit or do I need to set both SUID and GUID

does this give slightly more security? as if the process is compromised it now only has user level access?

The way you do that is to wrap your startup command utilizing **su**. You will tell it to 'switch user'. Root will still kick the script off, but will call the process as the specified user. 

[INDENT]**example: su neo -c *myprogram***[/INDENT]

runs *myprogram* as the user neo.

Shells usually expect a command to be one word, so if you have multiple words or a location just wrap that portion in a quotes. 

Hope that helps!

---

### Post by pab10 on 2009-03-10
yes, thanks.

is the su - option required?

I'll see if I can get xinetd to load sc_serv...

---

### Post by kryptikos on 2009-03-12
You shouldn't need to include the '-' unless your user that you want to run it as requires specific binary paths that are already coded in its $PATH.

---


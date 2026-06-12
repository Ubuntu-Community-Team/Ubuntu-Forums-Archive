---
title: "Auto Login without gdm"
date: 2009-04-13
forum: General Help
---

### Post by Augsburg on 2009-04-13
I'm having a hard time figuring this out.  If anyone could help that would be great.  I administer an ubuntu lab. I recently wrote a script that will allow a user to authenticate against a novell netware server, and login.
The script will run after a specific unprivelaged user has logged in.

I would like to have a setup where the computer boots directly to an already logged-on command prompt (no gdm, no login).  Then i will run the program.  This would be the ideal method, but i haven't yet found a way to do this.

The alternative to this method would be allowing a gdm login, but then making it so that the user who logged in must run my script and authenticate, or be logged out.  If this is to be the solution, how can i

a) cause everything else to stop working until script is completed (kind of like the sudo password prompt after clicking on something in the System>Administrator menu)

or

b) run a shell script that changes a global variable so that a daemon that runs on login can check to see if it is set (so that if the authentication script isn't run (a.k.a. the username and password aren't set) the daemon can time-out and logout the user).

Any suggestions or solutions to this problem would be great!  Thanks.

---


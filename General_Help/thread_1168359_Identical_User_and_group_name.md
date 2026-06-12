---
title: "Identical User and group name"
date: 2009-05-24
forum: General Help
---

### Post by rpaskudniak on 2009-05-24
Greetings.

I recently configured my Ubuntu 9.04 installation, a far cry form my disaster from last year (which left me too
timid to try anything while I needed this PC for work :frown:).  Now that I have had one success, I wish to move 
on to greater purposes.

I started writing this to ask a question.  As with my recent experience on the Symantec community forum, the
solution came to as I was typing the question; I tested each step before typing it.  So I offer it to the
community as a solution to a problem (however unlikely y'all are to encounter this), and inviting alternate,
easier solutions.

I want to to  install an Informix database server on my new box.  Similarly to PostgreSQL and Oracle, it demands a
user account named *informix*.  Informix also requires me to create a group named informix and that user
*informix* be the only member of that group. Therein lies my problem:

Using **users-admin**, I am able to create group informix.  Then, when it comes to creating the informix user
account, it complains that user informix already exists.  Of course, I know it does not yet.  Suspicion:
users-admin confuses the existence of the group informix with the new userid informix.  Sounds buggy to me, unless
someone can justify it.  Ragardless of any justification, it is something to worked around. 

_Workaround I_.
Operating on a hunch, I forcibly created the informix user account in /etc/passwd with the informix group ID I
wanted.

The problem with is is that, of course, user informix did not make it into /etc/shadow; I cannot log in as
informix because it always fails authentication.

_Workaround II_. 
My solution, which I detest as a kludge that will eventually bite me on the on the place where I sit:
[LIST=1]
[*]I deleted both entities - the informix userid and the informix group id.
[*]I created group iinformix, as opposed to group informix
[*]I recreated user informix as a member of group iinformix (with the typo). This succeeded. (no surprise)
[*]I now went back and recreated group informix.  No objection here.
[*]Next, I added user informix to group informix.
[*]Finally (or so I thought), I went back to user properties for user informix and set his (pardon the
anthropomorphism :-& ) primary to informix. No error message there so it looks successful, but..
[*]A check of /etc/group shows me that user informix is not listed as a member of group informix;
still on group iinformix only.  Whereas, the /etc/passwd entry for user informix shows me
the correct primary group.
[/LIST]
So my solution seems to be correct, despite the slight snag in the final item above.  I can su to 
informix or log in altogether from the desktop; the "id" command shows I am in the correct
 user group.

As I mentioned, I really don't like this solution and would welcome an easier one; this is not
the last ubuntu desktop I plan to configure.

Also, if someone can identify my initial obstacle as a bug, maybe it will get fixed. (I'm not at 
that level yet within this community.)  I also fear that my success will be seen as a bug and
someone might fix that, which would break my oh-so-clever :idea:scheme. (Looking for a sarcastic smiley..)

Opening the floor...

---

### Post by asmoore82 on 2009-05-24
> **rpaskudniak said:**
> Using **users-admin**, I am able to create group informix.  Then, when it comes to creating the informix user
account, it complains that user informix already exists.  Of course, I know it does not yet.  Suspicion:
users-admin confuses the existence of the group informix with the new userid informix.  Sounds buggy to me, unless
someone can justify it.  Ragardless of any justification, it is something to worked around.

The software's install process might have created the account for you.

In general, I would recommend a more Open product with a large and healthy community
such as PostgreSQL and MySQL if Oracle doesn't chopshop it now that they own it.

---

### Post by asmoore82 on 2009-05-24
> **rpaskudniak said:**
> _Workaround I_.
Operating on a hunch, I forcibly created the informix user account in /etc/passwd with the informix group ID I
wanted.

The problem with is is that, of course, user informix did not make it into /etc/shadow; I cannot log in as
informix because it always fails authentication.

root can edit /etc/shadow directly, make a 2nd copy of your user line and change the name to informix, then:
```
passwd informix #as root
```
to set the password(running `passwd` as root is special because it won't request the old password first).

---

### Post by rpaskudniak on 2009-05-26
> **asmoore82 said:**
> The software's install process might have created the account for you.

In general, I would recommend a more Open product with a large and healthy community
such as PostgreSQL and MySQL if Oracle doesn't chopshop it now that they own it.

Asmoore,
I am choosing Informix first because that is my specialty.  But I have not installed the Informix software yet.  And, having installed it on godzillions of host machines, I *know* it does not create an account for me.  Though I will confess to never having installed it as a package; it has always been via a big shell script.  I do not know if the download for Linux will be a package or a script.

Food for thought, though.  I'll have to check with the Informix forum.

Thanks.

---

### Post by rpaskudniak on 2009-05-26
> **asmoore82 said:**
> root can edit /etc/shadow directly, make a 2nd copy of your user line and change the name to informix, then:
```
passwd informix #as root
```
to set the password(running `passwd` as root is special because it won't request the old password first).

Asmoore,
I had tried setting the password as root after forcibly creating the user in /etc/passwd. :idea:

I don't recall the error but I do recall it didn't work.  I omitted it from my already-too-verbose missive.

Thanks for having the same idea, however.  It makes me feel less lonely.

---


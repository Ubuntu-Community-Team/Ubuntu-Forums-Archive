---
title: "Gutsy - how to start Evolution backup in a script"
date: 2007-10-19
forum: Desktop Environments
---

### Post by rogerdean on 2007-10-19
Morning folks

I've just happily upgraded to Gutsy, and am pleased to find Evolution has a new backup feature.

Until now I have been backing up using a script which just copies the .evolution folder along with everything else, but this never worked too well, especially with Evolution settings.

So my question is this - how do I invoke the Evolution backup facility in my script? What would the command be?

Cheers
Roger

---

### Post by tempel on 2007-10-21
I've been looking to do exactly the same thing, and after poking around evolution's man page and --help, i suspect that the -c (or --component) is the key.  However, i can find no documentation on what components can be used.  I'll keep looking and tell you if i get anything.

---

### Post by rogerdean on 2007-10-21
yeah that might well be right, or perhaps --component merely selects whether mail, contacts, tasks or whatever is active at launch...

anyway, fingers' crossed and thanks for the help!

---

### Post by rogerdean on 2007-10-21
i think that's not going to work i'm afraid... from the terminal

roger@roger-laptop:~$ evolution --component contacts

...brings up the contacts view, and...

roger@roger-laptop:~$ evolution --component tasks

...brings up the tasks view.

roger@roger-laptop:~$ evolution --component backup

...just brings a half-bare evolution screen, looking for a component called backup but not knowing one.

will keep looking...
R

---

### Post by tempel on 2007-10-21
Yeah, i had the same result and can't find any further documentation.
Well, in my script, i just have it open evolution so as to remind me to make the backup.  It works for me since i'll be sitting here triggering the update, but for remote or automated backup, it won't do the job.
Perhaps we just need to make a feature request for the next version?

---

### Post by rogerdean on 2007-10-22
good stuff, i've now done that. bugzilla Bug 488942.
cheers
Roger

---

### Post by rogerdean on 2007-10-22
i guess in the meantime we could use the unofficial Evolution backup deb, created by the guy who made Envy. I used it without problems for a month or two before the new Evolution made it obsolete (or so I thought!)
Have a look at [http://www.albertomilone.com/evolbck.html](http://www.albertomilone.com/evolbck.html)
It's not so slick (ie not integrated with evolution) but might work better from a script...

---

### Post by rogerdean on 2007-10-28
ok, i've been in touch with Alberto Milone, the creator of evolbck, and he's kindly agreed, in his own time, to make it possible to invoke his backup tool from the command line. Many thanks to Alberto!
I'll post back here when there's something to say...
Roger

---


---
title: "Question about KPPP error"
date: 2005-10-26
forum: Desktop Environments
---

### Post by L Campbell on 2005-10-26
I'm trying to get online with my newly installed Kubuntu and I am greeted with,
" Error - KPPP   /etc/resolv.conf  is missing or can't be read! "

I have tried reading through some of the questions others have asked, here and I often see the advice, " go to Terminal and type, etc., etc. ", so I suspect thats what I need to do.

However, I don't know where to find, or how to access, the "Terminal".

If someone could help me here I would really appreciate it.

Thanks.

Lewis.

PS  When I was loading the Kubuntu program, I saw the name of a file 'Bicycle repair'  (a subject dear to my heart) flash across the screen.  Where to I find that file?

**********

---

### Post by GeneralZod on 2005-10-26
[QUOTE=L Campbell]
However, I don't know where to find, or how to access, the "Terminal".
[/QUOTE]

K-Menu -> System -> Konsole

Sorry to disappoint, but the Bicycle Repair program is apparently:

"A refactoring tool for Python"

([http://bicyclerepair.sourceforge.net/](http://bicyclerepair.sourceforge.net/))

Hope this helps,
Simon :)

---

### Post by L Campbell on 2005-10-26
[QUOTE=GeneralZod]K-Menu -> System -> Konsole

Sorry to disappoint, but the Bicycle Repair program is apparently:

"A refactoring tool for Python"

([http://bicyclerepair.sourceforge.net/](http://bicyclerepair.sourceforge.net/))

Hope this helps,
Simon :)[/QUOTE]
................................

Thanks for your reply, Simon.

Old Monty Python, huh?  Whoda thunk it. :-)

I found Konsole and typed  /etc/resolv.conf/etc/  hit 'enter' and it tells me "no such file or directory"

Am I supposed to do something with any of the drop down menu tabs?

Kind regards.

Lewis.

***********

---

### Post by GeneralZod on 2005-10-26
Try typing (or copy-and-pasting!)

```

cat /etc/resolv.conf

```

and post the results here.  And no, there's no need to play with the drop down menu tabs if you don't want :)

It would probably be best if you took us through what happens from the moment kppp is loaded to the moment it gives you the error.

---

### Post by L Campbell on 2005-10-26
[QUOTE=GeneralZod]Try typing (or copy-and-pasting!)

```

cat /etc/resolv.conf

```

and post the results here.  And no, there's no need to play with the drop down menu tabs if you don't want :)

It would probably be best if you took us through what happens from the moment kppp is loaded to the moment it gives you the error.[/QUOTE]
*****************

Thanks for your patience, Simon.

Unfortunately I got the same result as previously with 'cat /etc/resolv.conf'

I went ' K menu - Internet - Internet dialup tool ' and the error message popped up.

" /etc/resolv.conf  is missing or can't be read!

Ask your system administrator to create this file (can be empty) with appropriate read and write permissions. "

I have Mepis running on another computer, so I'm comfortable with the KPPP applette.  When I close the error message, I tried configuring KPPP just as I normally do but when I try to 'query' the modem, it tells me, "unable to open modem".  I have tried changing ' /dev/modem ' to ' ttys0 ', ' ttys1 ', etc. but still nothing happens.

If you have time to write me back, I may not be able to respond until tomorrow, so please don't think I've lost interest in resolving this.   :-)

Kind regards.

Lewis.    (formally London, now Benbrook, Texas)

*************

---


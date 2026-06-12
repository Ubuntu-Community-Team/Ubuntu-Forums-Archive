---
title: "Can someone clever help me apply a fix to Ktechlab?"
date: 2009-03-24
forum: Education &amp; Science
---

### Post by zenithdave on 2009-03-24
Hi there, i have been playing with Ktechlab circuit simulation and am very impressed, however there is a bug which crashes the program when adding a new component in Intrepid. It's a reported bug that seems to have just been left idle although version 0.3.9 exists in the Repos and breaks Ktechlab when updated.

Version 0.3.6 works but is buggy and has less features so i just ignore the update to version 0.3.9 and at least get to play with it.

This is txt from someone who said they have fixed a bug but i do not have a clue what the poster is talking about also further down the thread someone confirms the fix does work!

"From: Slavko <slavino@slavino.sk>
To: [email]submit@bugs.debian.org[/email]
Subject: ktechlab crashes when component is added to the circuit
Date: Mon, 4 Aug 2008 11:15:57 +0200

[Message part 1 (text/plain, inline)]

Subject: ktechlab crashes when component is added to the circuit
Package: ktechlab
Version: 0.3-9
Severity: important

*** Please type your report below this line ***
When I try to add a component to a circuit board, the application
crashes (SIGSEGV).

After some investigation, I found a bug in the patch 40_g++-4.3.dpatch:
+       m_map = new ETMap( m_size );

I changed this line to:
+       m_map = new ETMap( m_size, std::vector<uint>( m_size ) );

ETMap is a vector of vectors of ints, it should be m_size x m_size, not
only m_size, but the original author didn't use the right C++ syntax,
which should be:

m_map = new ETMap( m_size, std::vector<uint>( m_size ) );

(Not only m_map = new ETMap( m_size, m_size ); )

It works fine after correcting this patch and rebuilding the package."

The thread here

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=49369](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=49369)

Can anyone translate what i need to do with the above txt as i would love to get this working properly :D

Thanks in advance, bit of a tall order i know.

---


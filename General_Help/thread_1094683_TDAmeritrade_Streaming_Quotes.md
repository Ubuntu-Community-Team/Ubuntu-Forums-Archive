---
title: "TDAmeritrade Streaming Quotes"
date: 2009-03-12
forum: General Help
---

### Post by ChessPlayer2486 on 2009-03-12
I'm wondering if there are any TDAmeritrade users who are also using Ubuntu who might be able to answer my question.  I would log into TD Ameritrade and then go to streamer and try to load it, the first small window would open and then it would load a black background, then thats where everything stops and nothing else loads.  Any ideas why?  Thanks in advance.

---

### Post by name_no on 2009-08-10
I have the same  problem.

I did install the icedtea plugin and at first it looked like it would work, windows came up with the right stuff in them, but within a couple seconds mozilla and the java windows go away.  So I disabled icedtea.

---

### Post by noe_name on 2009-08-13
This is how I got it to work.

1. Use the Synpatic Package Manager to add Java runtime 6  ( there are two choices - I picked something like platform dependent. )

2. Log into the TDameritrade.com account.

3. Try to open command center rather than streamer console. 

4. After giving it permission to open pop ups it will ask to install a plugin.   Chose Java 6.  Not the first choice which is icedtea.

( I choose icedtea the first time and it did not work, and later disabling it did not work.  It may have been because I did not have Java runtime installed but I also may have to not sure. )

For some reason, trying to open up the streamer console did not ask for a plugin.

After doing that, then the streamer console did open up properly.

---

### Post by sabai on 2009-08-17
It worked for me too, and after installing Java SE 6 instead of Icedtea, other streaming applets like that of Oanda also worked. Thanks for the useful advice.

---

### Post by 606david on 2009-09-21
YUP, had to get rid of icedtea and install reg sun java to get both to work for me, 9.04 on macbook pro.

kinda of a pain

---


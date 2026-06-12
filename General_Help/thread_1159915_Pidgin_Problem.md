---
title: "Pidgin Problem"
date: 2009-05-15
forum: General Help
---

### Post by gatoguts on 2009-05-15
Something weird happened to me in pidgin for the first time.  My friend (MSN protocol) sent me messages but I could not read them, i could only see some smilies and blank lines...i went to aMSN and the same thing happened with this friend but not with my other friends....what could have caused this?

---

### Post by bruno9779 on 2009-05-15
I would say a custom font used by your friend.

---

### Post by The-ITu on 2009-05-15
use aMSN
it rips!!

---

### Post by tombott on 2009-05-15
> **gatoguts said:**
> Something weird happened to me in pidgin for the first time.  My friend (MSN protocol) sent me messages but I could not read them, i could only see some smilies and blank lines...i went to aMSN and the same thing happened with this friend but not with my other friends....what could have caused this?

> **The-ITu said:**
> use aMSN
it rips!!

OP states that he tried aMSN as well, but I agree that its good!

As bruno9779 says, it sounds like a custom font issue.
Just out of interest try highlighting the message next time and see if you can see it or copy and paste it into Gedit.

Also try installing the msttcorefonts

```
sudo apt-get install msttcorefonts
```

---

### Post by TheExplorer on 2009-05-15
You may also try to set the encoding to **CP1251** in Pidgin. Modify Account -> Advanced Tab and put CP1251 in the **Encoding** field. Good Luck! That helped me to receive russian text when I'm offline. Otherwise it was unreadable.

---

### Post by gatoguts on 2009-05-15
> **tombott said:**
> OP states that he tried aMSN as well, but I agree that its good!

As bruno9779 says, it sounds like a custom font issue.
Just out of interest try highlighting the message next time and see if you can see it or copy and paste it into Gedit.

Also try installing the msttcorefonts

```
sudo apt-get install msttcorefonts
```

thanks i will try that...btw i was able to read it in ebuddy so it must be some new font she's using

---

### Post by gatoguts on 2009-05-16
> **tombott said:**
> OP states that he tried aMSN as well, but I agree that its good!

As bruno9779 says, it sounds like a custom font issue.
Just out of interest try highlighting the message next time and see if you can see it or copy and paste it into Gedit.

Also try installing the msttcorefonts

```
sudo apt-get install msttcorefonts
```

tombott i tried your suggestion to highlight my friend's message and guess what?  it works i can see it...why is that?  its a bit cumbersome to chat like that but it works  :p

---

### Post by gatoguts on 2009-05-16
well downloading the msstcorefonts didn't help...as a final footnote to this saga, i am chatting with my friend right now..i think she was using white colored font --that was the problem..white on white just doesn't work...she changed it to purple and everything is fine now;)

---


---
title: "Hindi Keyboard layout missing"
date: 2005-11-13
forum: Desktop Environments
---

### Post by LK-G on 2005-11-13
I can't find Keyboard Layout for Hindi/Devanagari when adding support for the same. It should come under India along with all other Indian languages but to my surprise, the same is absent. While I have seen in a few google searches, people talking about the same.

Have I missed something?

Thanks in advance.

---

### Post by LK-G on 2005-11-20
[QUOTE=LK-G]I can't find Keyboard Layout for Hindi/Devanagari when adding support for the same. It should come under India along with all other Indian languages but to my surprise, the same is absent. While I have seen in a few google searches, people talking about the same.

Have I missed something?

Thanks in advance.[/QUOTE]

I had posted this message few days back but I'm yet to get any answer on this. I had migrated from Fedora, which has excellent support for Hindi keyboard and other Indian languages. But ever since I came to Ubuntu I have tried installing many Indic/Devanagari/Hindi packages but hopeless.

While I see on the internet (google) that many people are using Hindi keyboard on Ubuntu but why its not there on my machine.

A few more things. I started with the Single Install ISO from Ubuntu site and then aded more packages using Synaptic. 

I CHOSE UBUNTU FOR ITS EXCELLENT PACKAGE SUPPORT BUT LACK OF SUPPORT FOR HINDI MEANS THAT I MAY HAVE TO BACK TO FEDORA.

---

### Post by LK-G on 2005-11-20
SOLVED!!!

To find the answer, I had to open /etc/X11/xkb/symbols/hi file and check why Hindi is missing. And I found that that Ubuntu people have given Hindi/Devanagri as the default language when one chooses India.

So if you choose India in the Keyboard Layout, you have chosen Hindi.

Not a Good Idea because, normally users try to locate a Language within Groups named by country names.

---

### Post by anil_robo on 2005-12-22
True. If I expand the country group called "India" I see many languages but not Hindi. If I collapse that group, only India remains. If I select the collapsed group called india, the keyboard layout preview shows Hindi characters! And I'm able to type in Hindi. Look here:


[IMG]http://img358.imageshack.us/img358/7599/hindiinput9fl.png[/IMG]

---


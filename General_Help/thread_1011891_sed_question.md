---
title: "sed question"
date: 2008-12-15
forum: General Help
---

### Post by spewperb on 2008-12-15
Hi all,

I'm trying to work out how to use sed.

I am basically using it to convert absolute file path to relative ones in a load of shake scripts (just text files really). 

Here is my command

sed 's:/Absolute/File Path/Goes/Here:../:g' source.shk > destination.shk

This doesn't seem to work though. It creates the destination.shk file and copies all the text from source.shk but it doesn't perform the string replace. The only thing I can think of is the string its looking for is in the middle of a load of text.

E.g.

GS_Node = SFileIn("/Absolute/File Path/Goes/Here", 31, "Auto", 1, 0, "v1.1", "0", "", 0);

Would this make any difference if so how can I fix this?

---

### Post by cmnorton on 2008-12-15
I believe sed -e is needed to execute an inline script.

What substitution do you want? I am not seeing that from your example.

---


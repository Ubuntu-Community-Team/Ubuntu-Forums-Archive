---
title: "E: Type 'eb' is not known on line 39 in source list /etc/apt/sources.list E: The list"
date: 2006-09-09
forum: Desktop Environments
---

### Post by girl176a1 on 2006-09-09
E: Type 'eb' is not known on line 39 in source list /etc/apt/sources.list E: The list of sources could not be read. Go to the repository dialog to correct the problem. 
I get this error please help me Im a newbie and I tried to put a repositorie of [http://www.wine.com](http://www.wine.com) in there so I could download Internet Explorer. Now Im in deep trouble can anyone help me. I get this message everytime I open Package manager. I cannot download any add or remove programs either. :( :confused:

---

### Post by petersjm on 2006-09-09
open a terminal window and type: sudo gedit /etc/apt/sources.list

and copy and paste the contents of the document in here. I might be able to help if I can see what the document says.

---

### Post by n.arciss.us on 2006-09-09
open a terminal and type ```
sudo gedit /etc/apt/sources.list
```

enter your password.

go to line 39 or look for a line beginning with "eb".

Put a d in front of that line so it say "deb" minus the quotes.

Save and close editor.

In terminal type ```
sudo apt-get update
```

Then ```
sudo apt-get install wine
```

I hope this helps!

---


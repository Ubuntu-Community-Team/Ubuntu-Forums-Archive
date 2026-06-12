---
title: "ahhh beryl"
date: 2007-06-15
forum: Desktop Effects &amp; Customization
---

### Post by Rufi0h on 2007-06-15
So The biggest problem right now is the white screen of death that i get when beryl tries to start. i can see it rotate slighly but all the screens are pure white, if i manage to click on something blindly a solid grey box appears. 

The main solution that i'm looking for right now is how to make beryl not start automaticly when ubuntu starts. everytime it starts it goes straight to the white screen, someone please help me fix this problem. 

Thanks.

---

### Post by L14UX_1NS1D3 on 2007-06-15
try logging into a fail-safe terminal and from there go to your /etc/init.d dir. 
from there locate your beryl startup  script.
cat into it and put a # at the beginning of every line, that should help or you could move the script or even delete it of you want.

---


---
title: "picasa question"
date: 2009-05-16
forum: General Help
---

### Post by 2roombas on 2009-05-16
Like most everyone else, I find Picasa to be a breeze to work with and I would like use it as my default photo manager.

I went into Systems -> Preferences -> File Management Preferences, click the Media tab and in the Photos box that says "Ask me what to do" I choose the "Open with other application" thinking I could simply choose Picasa.... but Picasa is not even in the list that pops up?! Why is that?

---

### Post by lovinglinux on 2009-05-16
I think it's because Picasa is implemented using Wine. So, it's not native. Anyway, I think you still can browse and select the Picasa executable.

---

### Post by 2roombas on 2009-05-16
> **lovinglinux said:**
> I think it's because Picasa is implemented using Wine. So, it's not native. Anyway, I think you still can browse and select the Picasa executable.

Hmmmm, I did a browse, then not knowing where to look typed "picasa" *no quotes)in the search. No picasa.exe ever showed in the list?!  What should I be looking for if not that?

---

### Post by oldos2er on 2009-05-16
On my system Picasa installed to /opt/google/picasa/picasa .

 If you run "which picasa" in a terminal it should tell you which directory it's in.

---

### Post by 2roombas on 2009-05-16
Ah, excellent, thank you!  I now found it in the opt/google folder, but I'm not sure where and which file is the executable one ?!  I'm new to linux and used to seeing that .exe, but thert is no .exe file here?!

---

### Post by 2roombas on 2009-05-16
oh... I got it now, thank you  After doing "which picasa" in terminal, I discovered it was in usr/bin/pivasa  Thanks again, it's all set now!

---

### Post by lovinglinux on 2009-05-16
> **2roombas said:**
> Ah, excellent, thank you!  I now found it in the opt/google folder, but I'm not sure where and which file is the executable one ?!  I'm new to linux and used to seeing that .exe, but thert is no .exe file here?!

The exe extension is a Windows only executable extension. Besides, in Linux you don't need an extension (most of the time) to open/execute a file with the correct application.

---


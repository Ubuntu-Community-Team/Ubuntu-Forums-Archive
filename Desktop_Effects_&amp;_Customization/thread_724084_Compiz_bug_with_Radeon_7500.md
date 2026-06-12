---
title: "Compiz bug with Radeon 7500"
date: 2008-03-14
forum: Desktop Effects &amp; Customization
---

### Post by Crashing on 2008-03-14
I have the ATi Mobility Radeon 7500 card in my laptop which came up with the same error message that the Compiz wiki said it would. Here's the instructions on how to fix it:
Users with the Radeon Mobility 7500 card may be unable to start Compiz due to an incorrectly detected maximum texture size; to solve this, create a file at /etc/drirc with the following contents, then restart X:

<driconf> 
<device screen="0" driver="radeon">
<application name="all">
<option name="allow_large_textures" value="2" />
</application>
</device>
</driconf>

The only thing is, it just says to "create a file" but doesn't say what to call it or what kind of file it should be. Does anyone know what to do here?

---

### Post by Crashing on 2008-03-14
I think I might have just figured it out....

---


---
title: "pulseaudio : connection refused"
date: 2009-04-23
forum: General Help
---

### Post by sefs on 2009-04-23
Hi i pulled out my sb card and re-enabled my internal via in the bios.  Now pulse audio isnt working.  I am getting a connection refused.

How do i get it back up and running

---

### Post by paradigm2 on 2009-04-23
First we should probably make sure the internal is even being seen now.

```

lspci -v

```

in a terminal.

---

### Post by sefs on 2009-04-23
> **paradigm2 said:**
> First we should probably make sure the internal is even being seen now.

```

lspci -v

```

in a terminal.


Thanks for your response.  I deleted the /home/myusername/.pulse folder.  It seemed to have in old info for the sound card I removed.

---

### Post by elitenoobboy on 2009-07-29
> **sefs said:**
> Thanks for your response.  I deleted the /home/myusername/.pulse folder.  It seemed to have in old info for the sound card I removed.

And thanks for your response! This fixed the problems I was having after a security update.

---


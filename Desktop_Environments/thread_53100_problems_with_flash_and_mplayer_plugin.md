---
title: "problems with flash and mplayer plugin"
date: 2005-07-30
forum: Desktop Environments
---

### Post by jeremytaylor on 2005-07-30
Hi there,
I've got a couple of small problems that I thought someone might know the answer to...

Flash animations on sites tend to work but are missing lots of the text, as these are normally the navigation bits it renders most flash heavy sites unusable...?

And...

Playing quicktime movies from within a webpage, the mplayer plugin starts up, buffers then says it is playing and the little ubuntu equivalent of an egg timer pops up. I'm wondering if this is because i have some of my mplayer settings set wrong... what video out device should i be using, many just seem to bring up error messages when i use them?

thanks for any help

Jeremy

---

### Post by david on 2005-07-30
Hi,

I had the same problem with Flash. Installing the gsfonts-x11 package fixed it for me. 

$ sudo apt-get install gsfonts-x11

---

### Post by jeremytaylor on 2005-07-30
fantastic worked straight away.
 thanks!

---


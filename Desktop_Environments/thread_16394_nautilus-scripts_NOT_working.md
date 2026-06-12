---
title: "nautilus-scripts NOT working"
date: 2005-02-21
forum: Desktop Environments
---

### Post by felipe on 2005-02-21
Hi,

I followed the wiki NautilusScripts howto, browsed GNOME forums and read many tips... but i can't just get most nautilus-scripts to work :/

I have some bash, perl and python scripts in ~/.gnome2/nautilus-scripts but only the python based are working, whether they are invoked with #!/usr/bin/python or with #!/usr/bin/env python. I am moticing this behaviour on both Warty and Hoary too

i tried everything suggested to make the bash scripts work, including:

checked, double checked and rechecked permissions
`mv script.sh script' (and back)
adding/removing a newline at the end of the script
adding/removing #!/bin/bash from the script as suggested somewhere

I can't understand why only python scripts show up in the menu, while nautilus doesn't even seem to see bash and perl scripts...

any idea why it runs fine with python scripts but fails with everything else?
many thanks :)

---


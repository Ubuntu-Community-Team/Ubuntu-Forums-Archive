---
title: "Nautilus freezes after being started"
date: 2008-06-17
forum: Desktop Environments
---

### Post by Marthr on 2008-06-17
Hi folks,

I'm having a problem with Nautilus in Ubuntu Hardy. At once my file manager didin't load totally anymore. If I opened my home folder it would show me an empty page and in a few seconds it would die on me. When I quit the window (forced) it did disappear, but within seconds it loaded my home directory again!

I had to remove Nautilus to use my desktop again and I'm now using Thunar to be able to do anything at all.

When I run Nautilus (after reinstalling it) from terminal it doesn't show me any errors.

I hope you can give me some hints in finding the exact problem. 

Thank you very much!

---

### Post by Marthr on 2008-06-17
Update:

I used a test account where I installed nautilus again. Everything worked fine and since I was experiencing this problem only in one account I removed '/home/user/.nautulis' completely. With confidence I started my main account again, but the problem percisted.  
Now I really don't know where to find the answer.

Hope this extra post is useful.

---

### Post by Marthr on 2008-06-17
Again an update:

I fixed the problem, but I'm still not happy with this solution. After checking out what exactly went wrong with Nautilus, my conclusion was that it must be the seahorse plugin. It was the last thing Nautilus loads when starting up.
So I removed the seahorse plugin from the '/usr/lib/nautilus/Extensions-2.0/' directory and everything works fine now, except for me missing the seahorse plugin.

Does this sound familiar? What can I do to get the plugin working again?

---


---
title: "tiresome 11.04"
date: 2011-05-09
forum: Desktop Environments
---

### Post by biloxi01 on 2011-05-09
Hello everybody!

I hate 11.04. There are some needless new function for example the new desktop which cannot be set with that ugly top and left panel (not removable or movable of course - how did the designers think about it? strange, fool, something like these - I haaaaaate), but I could agree to use classic view of ubuntu - it is perfect... It WAS perfect before 11.04. I cannot set up the old and fine working functionalities I need.

1; In gnome-terminal:
When you type and use file name which contains " " [space], the <tab> cannot write it correctly as in the old version: "\ ". I neeeeeeeeeeeeed! And everybody else needs, who uses terminal. How can I set it up? (It's unbelievable! I have to ask it!)

2; I do not know what's the name of the new function - just change the "function" expression to something censurable - at moving windows. If I want to place my window into a corner it changes to full screen view. I needn't!!! How can I set it  to work as normal instead of this stupid new way.

It's shocking!

Regards,
b

P.S.: Sorry for my invective. Can anybody help?

---

### Post by WthIteh on 2011-05-09
Hello and welcome to Ubuntu Forums :)
> **biloxi01 said:**
> 
1; In gnome-terminal:
When you type and use file name which contains " " [space], the <tab> cannot write it correctly as in the old version: "\ ". 
Could you tell an example file name? Since as I used gnome-terminal, the TAB key could complete names of files which have space in their name too! Maybe it's problematic for special file name!? (for example I typed "ll Op" and pressed TAB key and it completed it as "ll Open\ ModelSphere.desktop").
> **biloxi01 said:**
> 
2; I do not know what's the name of the new function - just change the "function" expression to something censurable - at moving windows. If I want to place my window into a corner it changes to full screen view.
Not a complete solution but a workaround: That window semi-maximizing function only will be triggered when your mouse pointer hit the screen edge. So you could put the window in corener without triggering that function, just by dragging window from some point that your mouse does not hit screen edge :)

---

### Post by biloxi01 on 2011-05-09
> Could you tell an example file name?No. It just works wrong in case of every file names, which contain space.

> Not a complete solution but a workaround: That window semi-maximizing  function only will be triggered when your mouse pointer hit the screen  edge. So you could put the window in corener without triggering that  function, just by dragging window from some point that your mouse does  not hit screen edgeI don't understand you - it is not true, but I want to set off this stupid function.

---

### Post by mcduck on 2011-05-09
Autocompletion works just fine for me as well. There's probably something wrong in your ~/.profile or ~/.bashrc files.

What comes to the window resize on screen edges feature, you can just disable the "Grid"-plugin in CompizConfig Settings Manager. Or adjust the thresholds to suit your taste.

---

### Post by biloxi01 on 2011-05-09
> **mcduck said:**
> Autocompletion works just fine for me as well. There's probably something wrong in your ~/.profile or ~/.bashrc files.
I've checked these. My .profile is a reference to my .bashrc and my .bashrc contains settings of terminal colors and a reference of /etc/bash_completion (should be a file), but there isn't any. There is a folder which called /etc/bash_completion.d/. I've checked the packages and everything looks correct.

> **mcduck said:**
> What comes to the window resize on screen edges feature, you can just disable the "Grid"-plugin in CompizConfig Settings Manager. Or adjust the thresholds to suit your taste.
I had to install this horror (compizconfig-settings-manager), but solved this problem. Thank You.

---


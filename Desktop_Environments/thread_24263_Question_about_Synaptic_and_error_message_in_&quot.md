---
title: "Question about Synaptic and error message in &quot;apt-get update&quot; command"
date: 2005-04-06
forum: Desktop Environments
---

### Post by cajunaggie on 2005-04-06
I just upgraded to Hoary and just for kicks ran the "apt-get update" command. I get this:
> W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: You may want to run apt-get update to correct these problems

What the heck?
And secondly where is Synaptic in Hoary? I can't find it in any of the menus.

---

### Post by lao_V on 2005-04-06
[QUOTE=cajunaggie]I just upgraded to Hoary and just for kicks ran the "apt-get update" command. I get this:

What the heck?
And secondly where is Synaptic in Hoary? I can't find it in any of the menus.[/QUOTE]

Did you run the apt-get update as suggested????

---

### Post by arctic on 2005-04-06
could you please give detailed information on what you have done so far for updating your system?

try the following thing nonetheless. open a terminal and try to run synaptic. do you receive any error messages?
are your update mirrors still directed at hoary? just an idea as they are not ponting to the original ubuntu servers...

---

### Post by BloGTK on 2005-04-06
[QUOTE=cajunaggie]I just upgraded to Hoary and just for kicks ran the "apt-get update" command. I get this:

What the heck?
And secondly where is Synaptic in Hoary? I can't find it in any of the menus.[/QUOTE]
 It appears to be a problem with the nerim.net repositories. If you're using Hoary sources, you shouldn't need to use the nerim sources - in general, I'd avoid it unless there's something there that you **really** need.

---

### Post by Leif on 2005-04-06
You need to generate the PGP keys for merillat. Please look it up in the forums/wiki, I know it's been posted before.

---

### Post by cajunaggie on 2005-04-06
[QUOTE=lao_V]Did you run the apt-get update as suggested????[/QUOTE]
Yes, and it gave me the same error message.

[QUOTE=artic]could you please give detailed information on what you have done so far for updating your system?

try the following thing nonetheless. open a terminal and try to run synaptic. do you receive any error messages?
are your update mirrors still directed at hoary? just an idea as they are not ponting to the original ubuntu servers...[/QUOTE]
I dist-upgraded to Hoary and then did everything in the Post-Update section of the Upgrading to Hoary page and rebooted. I'm currently running the Ubuntu Update manager and Synaptic showed up after I rebooted the computer. I'm gonna try fiddling with that next.

[QUOTE=BloGTK]It appears to be a problem with the nerim.net repositories. If you're using Hoary sources, you shouldn't need to use the nerim sources - in general, I'd avoid it unless there's something there that you really need.[/QUOTE]
So, how do I go about doing that?

[QUOTE=Leif] 	You need to generate the PGP keys for merillat. Please look it up in the forums/wiki, I know it's been posted before.[/QUOTE]
Do what with the what now?


In conclusion, I know, it says newbie for a reason. ](*,)

---

### Post by Locomorto on 2005-04-07
try running the automate script in the HOWTo and FAQ section, i used it and it got me the keys among other things automatically. It works quite well and i suggest you use it.

---

### Post by jeremy on 2005-04-07
[http://ubuntuforums.org/showthread.php?t=22279](http://ubuntuforums.org/showthread.php?t=22279) has instructions for generating keys

---


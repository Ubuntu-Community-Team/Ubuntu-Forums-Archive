---
title: "compiz on feisty fawn"
date: 2007-04-29
forum: Desktop Effects &amp; Customization
---

### Post by Metalclay on 2007-04-29
well...i previously had  beryl on my install of feisty fawn. after too much tinkering, i somehow disabled my wireless card (which i had to get to work using tuts).

anyway, i've read compiz is more stable, and is gonna merge with beryl anyway. soo...i wanna instlall it instead of beryl. i went to the website, and went to the downloads.

i download the compiz-0.4.0.tar.bz2 and...i don't know what to do with it xD

i looked for alternate methods, but i don't know how to use "git" or "cogito" and...for the binary option...i don't know where my source.list is...so i couldn't possibly add:

deb [http://gandalfn.club.fr/ubuntu](http://gandalfn.club.fr/ubuntu) feisty motu

i tried putting it in the terminal...nothing happened =(

oh well....any help or tut is appreciated. thanks.

also...i'm using an ati radeon card. i had to do alot of research to get it to work with beryl. is ati also a problem for compiz?

---

### Post by rolf-c on 2007-04-29
> **Metalclay said:**
> 
i looked for alternate methods, but i don't know how to use "git" or "cogito" and...for the binary option...i don't know where my source.list is...so i couldn't possibly add:

deb [http://gandalfn.club.fr/ubuntu](http://gandalfn.club.fr/ubuntu) feisty motu


You can add that repository directly to your Synaptic Package Manager by:

1.)  Click on System -> Administration -> Synaptic Package Manager

2.)  Enter your password as requested

3.)  Click on Settings -> Repositories

4.)  Click on the Third Party Software tab

5.)  Click on Add and read the short instructions - you are going to type in here this text:

deb [http://gandalfn.club.fr/ubuntu](http://gandalfn.club.fr/ubuntu) feisty motu

6.)  Click Add Source, Close

7.)  Click the Reload button in Synaptic to get the newly added repo info.

Now, this has added the repository but what you do with it is beyond the scope of my reply.  I assume the package(s) you are looking for are in this repository.  Use the Search function to find them by name.

As an FYI, your sources.list file is in /etc/apt and is the file Synaptic reads to find repositories.  You could also edit this file directly and insert the repository information here, then from the shell prompt type 'sudo apt-get update' to refresh.

---

### Post by Metalclay on 2007-04-30
cool, thanks for the help.

but...i got this error: 

W: GPG error: [http://gandalfn.club.fr](http://gandalfn.club.fr) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CBF6E0B8483170E9

any tips?

i also tried an alternate method via terminal and got:

W: GPG error: [http://gandalfn.club.fr](http://gandalfn.club.fr) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CBF6E0B8483170E9
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by wayne8 on 2007-05-10
K since you are asking about Compiz on Feisty I am guessing that you have Feisty. That being the case you can simply obtain Compiz by System---> desktop effects--->enable. 

Here are some websites to get you started with it.
[https://help.ubuntu.com/community/CompositeManager/ConfiguringCompiz](https://help.ubuntu.com/community/CompositeManager/ConfiguringCompiz)
[http://compiz.org/FAQ/Users#Why_can.27t_I_get_the_cube_rotation_to_work.3F](http://compiz.org/FAQ/Users#Why_can.27t_I_get_the_cube_rotation_to_work.3F)

Good Luck.

---


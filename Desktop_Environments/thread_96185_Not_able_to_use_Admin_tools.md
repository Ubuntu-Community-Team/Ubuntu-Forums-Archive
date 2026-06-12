---
title: "Not able to use Admin tools"
date: 2005-11-28
forum: Desktop Environments
---

### Post by venkatachar on 2005-11-28
Hi, 
  When i try to the change time or try to  open Synaptic from the Menu, it asks for the password , even after entring the password the Ui (ie, Synaptic  etc ) dosent popup.
Thanks in advance 
Venkatachar

---

### Post by venkatachar on 2005-11-28
Hi, 
  When i try to the change time or try to  open Synaptic from the Menu, it asks for the password , even after entring the superuser password the Ui (ie, Synaptic  etc ) dosent popup.
Thanks in advance 
Venkatachar

---

### Post by Hairy_Palms on 2005-11-28
what happens if u type sudo synaptic in a terminal?

---

### Post by from Vienna on 2005-11-28
Hello, all together!

>what happens if u type sudo synaptic in a terminal?

I have the same problem (same 5.10). 

Nothing happens.

---

### Post by venkatachar on 2005-11-28
I can open it from trminal as superuser. Thats how i am using it now. While installing i made the default user (first user which i yped during installation) as "root" .

Can this cause a problem?

---

### Post by dcstar on 2005-11-28
[QUOTE=venkatachar]I can open it from trminal as superuser. Thats how i am using it now. While installing i made the default user (first user which i yped during installation) as "root" .

Can this cause a problem?[/QUOTE]
Possibly, the "root" user would already be created by the installation (but left with login disabled), so having you create it could have created all sorts of complications.

If you don't have anything important on your Ubuntu installation, I would recommend you start again (and this time, create another user name for your default).

---

### Post by venkatachar on 2005-11-29
Thanks david for your reply, but  reinstalling will be my last option .Will wait for some more time , if anyone else has the solution.

---

### Post by Kapre on 2005-11-29
[QUOTE=venkatachar]Hi, 
  When i try to the change time or try to  open Synaptic from the Menu, it asks for the password , even after entring the password the Ui (ie, Synaptic  etc ) dosent popup.
Thanks in advance 
Venkatachar[/QUOTE]

venkatachar - try the approach on this [thread]("http://www.ubuntuforums.org/showthread.php?t=96880")

---

### Post by hashimoto on 2005-11-30
I think you (as user) are not in the sudoers file. Open terminal, do "su" and then "visudo". Add your username to the end with the same options as previous line has (somethin in line with "ALL (ALL)" etc).

Hope this helps

---


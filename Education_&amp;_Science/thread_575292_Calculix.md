---
title: "Calculix"
date: 2007-10-13
forum: Education &amp; Science
---

### Post by basilwatson on 2007-10-13
Has anyone managed to get calculix installed on a fiesty?
I have the install instutions in front of me ,,,but I am getting confused 

If it s heading towards the 2 hard basket, is there a FEA package out there??
open source and working?

could some kind soul point me in the rigjt direction 

Stephen

---

### Post by parhyang on 2008-06-30
ok try this, save calculix(ccx/cgx) to /home/"yourname" right click tar.bz2 then extraxt there. rename ccx_1.x to ccx. change permision by right click again, then start Appplication-->Accessories-->Terminal type comand : sudo mv /home/"yourname"/ccx /usr/local/bin/ do the same thing too for cgx executable files. try cgx -b dummy.fbd the GUI window should be shown.

---

### Post by strollerdude1 on 2008-09-28
Thank you parhyang,

This method worked well for cgx (well it worked as you suggested but the gui window doesn't operate too well) however when I try to use ccx I get the following message. I'm using hardy heron.

$ sudo ccx spring5.inp
/usr/local/bin/ccx: 1: ELF: not found
/usr/local/bin/ccx: 2: @: not found
/usr/local/bin/ccx: 3: CU
                           : not found
/usr/local/bin/ccx: 4: Syntax error: word unexpected (expecting ")")

I will try to find a solution, but would appreciate any assistance.

Strollerdude

---

### Post by Xnst on 2008-09-28
Hi,

I think the new version, 1.8, only have ccx binaries for the 64 bit architecture. You probably need to compile it yourself.

I suggest you check out the Calculix e-mail list.

[http://groups.yahoo.com/group/calculix/]("http://groups.yahoo.com/group/calculix/")

In the archive you see several suggestions how to compile for a 32-bit machine.  

If you are looking for FE-software you could try Salome. There is another thread for that:

[http://ubuntuforums.org/showthread.php?t=605625&highlight=salome+fe]("http://ubuntuforums.org/showthread.php?t=605625&highlight=salome+fe")

Good luck

---

### Post by tuvw962 on 2008-10-02
[wow gold](http://www.mmoinn.com)A preacher was telling his congregation that anything they could think of, old or new, was discussed somewhere in the Bible. The entirety of the human experience could be found there, without exception.After the service, the preacher was approached by a woman who said, "Preacher, I don't believe the Bible mentions PMS."The preacher replied that he was sure it must be there somewhere and that he would look it up.The following week, after service, the preacher called the woman aside and showed her a passage which read ..."And Mary rode Joseph's *** all the way to Bethlehem." [world of warcraft gold](http://www.mmoinn.com/) [warhammer gold](http://www.gold-warhammer.com/) [wow power leveling](http://www.mmoinn.com/mmoinn_pl/)[http://www.mmoinn.com](http://www.mmoinn.com/)

---

### Post by parhyang on 2009-03-30
yup, you're right Xnst.
thanx for correct me, I just try cgx only and play a bit GUI.
since you mention i try build from source, install libs dependcs etc. but i still fail to compile. until good guys "Peter Schaefer" post in calculix@yahoo group.

deb [http://roe10.physik.hu-berlin.de/CalculiXDebianPackages/binary]("http://roe10.physik.hu-berlin.de/CalculiXDebianPackages/binary")

hmm. it's work for U8.1 on my netbuks,thx. :popcorn:

about:salome_meca its works too, but the analysis of code_aster is not easy, i'm non french speaks :(

---


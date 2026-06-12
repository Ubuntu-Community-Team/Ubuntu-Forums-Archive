---
title: "Virtualbox extension pack and unknown Password?"
date: 2012-08-14
forum: Desktop Environments
---

### Post by Neill_R on 2012-08-14
[B]SOLVED Re: Virtual box error NS_ERROR_FAILURE (0x80004005)

on a Ubuntu 12.04 server 32b + Ubuntu-desktop 

[/B]             
                                                                I am getting this error when I try to install the extension pack 

virtualbox 4.1.12_ubuntu r77245
oracle _VM_VirtualBox_Extention_pack-4.1.12-77245.vbox-extpack 

I accept license agreement 

Asks for Administrative password Black screen centered gray box 



[COLOR=Red]None of my password work here[/COLOR]

installer failed error code 255

 p, li { white-space: pre-wrap; }     Result Code: 
  NS_ERROR_FAILURE (0x80004005)
   Component: 
  ExtPackManager
   Interface: 
  IExtPackManager {3295e6ce-b051-47b2-9514-2c588bfe7554}
                                                                                                   [IMG]http://ubuntuforums.org/images/rebrand/statusicon/user_online.gif[/IMG]                            [[IMG]http://ubuntuforums.org/images/rebrand/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=12171018")                                                                                    [[IMG]http://ubuntuforums.org/images/rebrand/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=12171018")                                        [[IMG]http://ubuntuforums.org/images/rebrand/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=12171018")                               [[IMG]http://ubuntuforums.org/images/rebrand/buttons/multiquote_off.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=12171018")                               [[IMG]http://ubuntuforums.org/images/rebrand/buttons/quickreply.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=12171018")                                                                                                                                                                                                                          [CENTER]         [New Reply       ]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=12171018")[/CENTER]

---

### Post by unevenflow on 2012-08-14
Hey, it requires your user password if this doesn't work you could try the newer version: virtualbox-4.1_4.1.18-78361~Ubuntu~precise_i386.deb  + Oracle_VM_VirtualBox_Extension_Pack-4.1.18-78361.vbox-extpack

---

### Post by Neill_R on 2012-08-14
Solved

I had install virtualbox as an Active Directory user the root user (installing ubuntu user***rootusername  ***) did not have vboxusers group once that was done

***sudo usermod  -G         adm,cdrom,sudo,dip,plugdev,fuse,lpadmin,sambashare,vboxusers rootusername ***

FYI I am using Centrify Express so that the ubuntu pc can attach to the Active Directory Domain

---


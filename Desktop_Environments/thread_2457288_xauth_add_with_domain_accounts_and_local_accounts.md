---
title: "xauth add with domain accounts and local accounts"
date: 2021-01-29
forum: Desktop Environments
---

### Post by bfrown1221 on 2021-01-29
[FONT=&amp]System setup:[/FONT]
[FONT=&amp]Ubuntu 20.04 LTS

Ubuntu MATE desktop setup[/FONT]
[FONT=&amp]userA = local account[/FONT]
[FONT=&amp]userB = domain account[/FONT]
[FONT=&amp]userC = local account[/FONT]
[FONT=&amp]System joined via SSSD[/FONT]
[FONT=&amp]homedir created using oddjob[/FONT]
[FONT=&amp]Using x2go client to get GUI desktop[/FONT]
[FONT=&amp]GUI desktop is MATE[/FONT]
[FONT=&amp]
[/FONT]
[FONT=&amp]Issue:[/FONT]
[FONT=&amp]UserB logs in with their domain account, then I have them do the following:[/FONT]
[FONT=&amp]1)Xauth list $DISPLAY[/FONT]
[FONT=&amp]2)Xhost +[/FONT]
[FONT=&amp]3)Sudo su &#8211; oper[/FONT]
[FONT=&amp]4) Xauth add step 1 output[/FONT]
[FONT=&amp]5) export DISPLAY=: &#8220;Number from step 1&#8221;.0[/FONT]
[FONT=&amp]6)xclock[/FONT]
[FONT=&amp]At step 4 however they get an xauth timeout saying that it can't "Timeout in locking authority file /home/userB/.Xauthority"[/FONT]
[FONT=&amp]
[/FONT]
[FONT=&amp]This however works if I log in userC, do the above steps and swap to userB and I can run xclock or any other GUI program. Not sure why it's not working when it comes to a domain account though. I've read that setting +x on .Xauthority could help for group/others but that's set and still doesn't work.[/FONT]
[FONT=&amp]Xauthority is owned by userB and group "domain users". userA is not in domain users since it's a local account but I have Xauthority set for others to be able to execute as well.[/FONT]
[FONT=&amp]I have also tried using 2 domain accounts, swapping from 1 to the other and doing an xauth to determine if 2 domain accounts could share a display and that does not work either. [/FONT]
[FONT=&amp]I've also tried blowing away the Xauthority file, and recreating it as root, giving it proper permissions and logging back in as userB and still nada[/FONT]
[FONT=&amp]
[/FONT]
[FONT=&amp]This worked perfectly fine on Centos8 but swapped system to Ubuntu and now it doesn't.[/FONT]

---


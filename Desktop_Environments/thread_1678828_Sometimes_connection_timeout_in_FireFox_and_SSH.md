---
title: "Sometimes connection timeout in FireFox and SSH"
date: 2011-01-31
forum: Desktop Environments
---

### Post by khosro on 2011-01-31
Hi,
Since two weeks ago,at work,i have sometimes connection timeout in my Firefox to visit some website ,such as [http://seamframework.org]("http://seamframework.org/") in my laptop,but i can see website like Google.But i have not the same problem with other computer in our network(Their OS are either Ubuntu or Windows).And also when i want to SSH to our server(it is located outside of our country) i got the same error(connection timeout) and again i do not have problem when i use another computer in the same network.But at home i do not have such problems.I am really confusing ,why this problem occurred!!!!????:mad:
It is also to mention that ,i use different ISP in work and home,but i think ,it does not related to ISP because other computers at work in the same network that use the same ISP do not have this problem.
And also i have searched in forum to find a solution and i found some posts regarding this problem,but none of them helped me.

Khosro.

---

### Post by prshah on 2011-01-31
> **khosro said:**
> sometimes connection timeout in my Firefox to visit some website,but i can see website like Google.

Hi, I had a similar problem, you can take a look at my [(solved) post]("http://ubuntuforums.org/showpost.php?p=4514356&postcount=12") on this for a possible solution; you could also [review the entire thread]("http://ubuntuforums.org/showpost.php?p=4514356").

Hope it helps:

---

### Post by khosro on 2011-01-31
Hi,
Thank you.I read entire post and i changed MTU from 1500 to 1492 and also to 1400 but without any success.And i also changed MTU by this command : 
```

sudo ifconfig eth0 mtu 1492

```but without any success.

and this is my output : 
```

root@khosro-laptop:~# tracepath www.seamframework.org
 1:  khosro-laptop                                         0.250ms pmtu 1492
 1:  192.168.1.1                                           2.192ms asymm  2 
 1:  192.168.1.1                                           1.908ms asymm  2 
 2:  91.186.200.193                                       80.579ms 
 3:  10.0.0.229                                           56.086ms 
 4:  10.0.0.228                                           66.960ms 
 5:  10.0.0.226                                           89.971ms asymm  6 
 6:  10.0.0.225                                           77.636ms asymm  5 
 7:  10.10.10.1                                           81.298ms 
 8:  217.218.146.141                                     112.582ms 
 9:  195.146.63.253                                       69.351ms 
10:  ldn-b1-link.telia.net                               214.645ms asymm 17 
11:  ldn-bb1-link.telia.net                              230.350ms asymm 17 
12:  ash-bb1-link.telia.net                              286.088ms asymm 18 
13:  atl-bb1-link.telia.net                              316.231ms asymm 19 
14:  internap-ic-140160-atl-bb1.c.telia.net              305.708ms asymm 18 
15:  border11.tge4-1-bbnet2.acs.pnap.net                 303.617ms asymm 18 
16:  qts-36.border11.acs.pnap.net                        336.470ms asymm 14 
17:  no reply
18:  no reply
19:  no reply
20:  no reply
21:  seamframework.org                                   386.175ms !H
     Resume: pmtu 1492 
root@khosro-laptop:~# 


```It seems i must reinstall Ubuntu.


Khosro.

---


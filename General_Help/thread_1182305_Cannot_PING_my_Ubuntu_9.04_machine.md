---
title: "Cannot PING my Ubuntu 9.04 machine"
date: 2009-06-08
forum: General Help
---

### Post by asusx on 2009-06-08
Hello guys,
As the title states, I cannot ping my Jaunty machine from another computer on the network. I'm pretty sure I don't have any firewall installed. Any ideas?

---

### Post by Ocxic on 2009-06-08
post the output of "sudo iptables -L"

---

### Post by asusx on 2009-06-08
Thanks for reply... I've disabled ufw. Ironically after posting this thread, I'm able to ping my ubuntu machine. I've noticed that it wasn't only the ping problem, I couldn't connect to mpd. Looks like it's solved now.

---

### Post by asusx on 2009-06-08
Looks like the problem persists. The only time i can ping is for some time after pinping from my ubuntu pc. I believe I have ufw disabled. Anyway,  here is my output of "sudo iptables -L".

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination

---

### Post by Ocxic on 2009-06-08
try "sudo iptables -F"  that will clear the firewall completely

---

### Post by asusx on 2009-06-08
no luck... Right now I'm using my Ipod to control the mpd and the only way i can connect is to ping my ipod. After pinging it works for some time. Alse, I'm sure that the Ipod program is not the reason as it works on my ubuntu 8.04. Any other reasons it might not work?

---

### Post by asusx on 2009-06-08
bump! Anyone?

---

### Post by asusx on 2009-06-09
Bump!

---


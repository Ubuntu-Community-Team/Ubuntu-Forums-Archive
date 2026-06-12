---
title: "need help with php script to start sshd"
date: 2009-03-29
forum: General Help
---

### Post by SanZoR on 2009-03-29
Hello,
I dont know what is wrong with this script below:
[PHP]<?php 
$shell_cmd = "export TERM=vt100;\n"; 
$shell_cmd = "sudo -i << PASSWORD\n"; 
$shell_cmd .= "/etc/init.d/sshd start;\n";  
shell_exec($shell_cmd); 
?>[/PHP]
What is wrong? :(
Thanks in advance!

---


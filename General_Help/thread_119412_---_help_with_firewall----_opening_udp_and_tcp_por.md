---
title: "--- help with firewall---- opening udp and tcp ports"
date: 2006-01-19
forum: General Help
---

### Post by njzillest on 2006-01-19
i need help opening my tcp and udp ports. Im a linux n00b. im not able to connect to the servers on ML donkey, such as gnetlla, and fasttrack. Is there a fire wall in ubuntu block my tcp and udp ports. 




thanx for the help 

=

---

### Post by bulldogzerofive on 2006-01-19
I think IPtables is there but not configured to block anything, unless you already installed something.

Either way, you can just "sudo apt-get firestarter" or "sudo apt-get guarddog and mess with its configuration to your heart's content.

However, methinks you might want to confirm that you have your p2p software set up correctly before you go down this path.

---


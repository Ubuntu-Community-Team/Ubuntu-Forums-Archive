---
title: "About the Ubuntu firewall -- again"
date: 2009-05-09
forum: General Help
---

### Post by GL_NORWAY on 2009-05-09
Ok, I guess you guys are getting sick of noobs asking about the Ubuntu firewall :P but I just want to know if I've understood it correctly _once and for all_ since I appreciate security.

Let me just compare it to my DSL router that I've managed to understand somewhat: When I log on to this box, I have a firewall section. The firewall can be turned on and off with a button. One time I did a test by turning it off and looked at a software firewall in XP that I installed for testing purposes. Not long after, this software firewall started to show some attacks from the wide open internett. As soon as I turned the DSL router's firewall on again with its simple button, the attacks reported by the software firewall stopped and never came back. So the firewall in that box is therefore always ON.

But the DSL router's firewall also have more advanced options. One option is to make rules, or whatever it should be called, and this list of rules is empty. If I make a new rule to block all ports, I can't even surf the web. If I open port-80, I can surf the web but not connect to MSN. If I enable port-443 I can connect to MSN. And etc. But even when all ports are "open", or no rules if you want to, the firewall still block attacks from the outside.

So....

Does the Ubuntu firewall (UFW/iptables) work the same way and block outside attacks even when no rules are applied and no commands are entered after install? Or do I need to $ sudo ufw enable, to turn it on? Or enter any other commands to activate it?

I know that I have a firewall in my DSL router, but sometimes I'll need to connect to the net without a HW firewall. So it's important for me to understand how the Ubuntu firewall works.


Thanks in advance for help and patience!

---

### Post by 3rdalbum on 2009-05-09
You say that your router was "blocking attacks". Were these attacks actually on ports that your software was listening to? If not, if the attacker was trying to attack a port that nothing was listening on, then a firewall won't really do anything. It's like if a man 50 metres away from you starts throwing punches in the opposite direction to you. You don't need to run over and block his punches, because he's not in any position to hurt you in the first place.

Leave your router's firewall turned on, and don't worry about setting outbound rules. Outbound firewalls are there to try and stop viruses that you already have from contacting the internet; since you're on Ubuntu, you don't have any viruses. Set up your router to block all incoming connections and allow all outgoing connections.

UFW is not enabled at install, but yes "sudo ufw enable" will enable it and block all incoming connections. If you're behind your router's firewall, then there's no point unless you don't trust your own network's traffic.

Firewalls aren't designed to "block attacks" - they are not that smart/foolish. They block connections, whether desirable or malicious. That's why they are so effective - they don't need to keep a list of "what sorts of connections are bad" and keep it up-to-date, they just keep a list of "what ports can I allow connections from".

---


---
title: "logging in on external home folder (changing uid rights)"
date: 2009-03-11
forum: General Help
---

### Post by Bloemetjesgordijn on 2009-03-11
Hi guys,

I have two computers in my house:
[LIST]
[*]Computer A (htpc)
[*]Computer B (game pc)
[/LIST]
What I would like to do is to make use an external home folder on A with computer B (and thus resulting in login on A via computer B).

The following I have done:
1) I have 'linked' /home/htpc (of A) to /home/htpc (on B) with use of NFS (this works).

*When I go to /home/htpc on computer B it is in fact /home/htpc on computer A

2) I have made a user on computer B identical to the user on computer A
(for instance both with username "htpc" and password "1234") 

When I switch user on B and login with user account of A I get an permission error.

I have googled around and it seems that user this is due difference "uid" 

This might be right:
on A user "htpc" has uid 1000
on B user "htpc" has uid 1003

Now comes the question:
How do I change set the uid rights on computer A to accept both uid's (1000 and 1003)??

This should be possible with chown....but i dont know how.

Greetz

Boemetjesgordijn

---


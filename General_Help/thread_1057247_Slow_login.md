---
title: "Slow login"
date: 2009-02-01
forum: General Help
---

### Post by choochus on 2009-02-01
I've searched these forums and Google for an answer, but nothing matches these symptoms.

When I either log into my Ubuntu system remotely, locally, or use the su command there is a 20-30 second pause before I get a command prompt. This happens no matter what user I log in as.

The pause occurs before /etc/profile is touched. Watching ps it happens before the user launches any processes. Watching top I don't see any processes start during login.

I don't see errors in any logs, and worse, I don't know which component could be causing the problem, so I don't know what log settings to change.

I've walked through the steps from posts that suggest changes to SSH, SMB, DNS, and PROFILE, but none of these have any effect.

The problem seems to have started when I upgraded to Ubuntu 8.10 a few weeks ago.

Any help is much appreciated!

 -Chooch

---


---
title: "Hot corners stopped working alltogether"
date: 2015-05-07
forum: Desktop Environments
---

### Post by paulhinterberger on 2015-05-07
Hey all,
I keep having issues with hot corners. I run Ubuntu 14.04 LTS after having small annoyances with 15.10 I switched back.
I use hot corners for Showing workspaces and for scale/spread all windows. I do this using a mix of Unity Tweak, CCSM and dconf-editor. I know this isn't ideal but so far worked for me until yesterday.

Issue yesterday: Whenever I used super+w or my lower left hot corner for spreading all windows, Unity seemed to crash and I find myself back at the login-screen. (The showing all workspaces kept on working though) I solved this by a switch in the dconf-editor: org->compiz->profiles->unity->plugins->core, my last three entries were ordered as follows:
"unityshell","expo","scale" which worked fine for me before but yesterday it gave me the above mentioned error. My solution was to switch it so that "unityshell" would be last.

Issue today: I ran updates this morning (apt-get update, apt-get upgrade) and rebooted. afterwards hot corners stopped working alltogether. I switched them on and off in Unity tweak, which used to help before, but this time it doesn't. So I tried switching my dconf-order again but I get the same error I got yesterday, so now I am a bit at a loss of what to do.

If it helps, my dconf-order now looks as follows: 
['core', 'composite', 'opengl', 'copytex', 'compiztoolbox', 'commands', 'vpswitch', 'regex', 'resize', 'imgpng', 'wall', 'place', 'move', 'mousepoll', 'snap', 'animation', 'unitymtgrabhandles', 'workarounds', 'session', 'fade', 'ezoom', 'expo', 'scale', 'unityshell']

Hope someone has an idea, let me know if you need any further information.
Cheers,
Paul
PS: I'd also love to use the show desktop hotcorner but I get the much discussed mouse-positioning error, if someone has a solution for that as well "while we're at it", all solutions I found didn't help me.

---

### Post by paulhinterberger on 2015-05-07
somehow this resolved itself

---


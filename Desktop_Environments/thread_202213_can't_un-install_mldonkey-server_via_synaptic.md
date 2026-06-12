---
title: "can't un-install mldonkey-server via synaptic"
date: 2006-06-23
forum: Desktop Environments
---

### Post by dronepower on 2006-06-23
I can't un-install mldonkey-server via synaptic.
If I try that I get the following error:

E: mldonkey-server: subproces pre-removal script gave back error value 1 


In boot manager I de-activated the auto start of this program, so running mldonkey services can't be the problem I think.

some of you had the same problem?

thanks,

---

### Post by vpervouchine on 2006-06-25
Hi,

I had the same problem until I came across this thread:
[http://ubuntuforums.org/showthread.php?t=201785]("http://ubuntuforums.org/showthread.php?t=201785")

I think the problem is that mldonkey doesn't start because of that error in startup script. And apt-get tries to stop it first, but since it's not running the attempt to stop it fails, and apt-get thinks it cannot proceed after that.

On my PC, I edited /etc/init.d/mldonkey-server and commented the line that stops mldonkey server, so that the script doesn't try to stop the server and hence doesn't return failure :) After that apt-get remove mldonkey-server worked just fine.

---


---
title: "Strange behaviour of the X process"
date: 2006-07-13
forum: Desktop Environments
---

### Post by mtausig on 2006-07-13
My X Server is behaving rather strange
 ps shows the X process correctly, but neither does "sudo killall X" do anything ("no process killed") nor does "ps -C X -o pid=" (should output the PID of the process) print anything. The only way top stop the server is "kill 1234".
Does anybody know why it does that and how to resolv it?

I am using Dapper, but experienced the very same behaviour on a Debian/Woody Box.

---


---
title: "Cannot run xterm -display localhost:0.0"
date: 2008-03-07
forum: Desktop Environments
---

### Post by jinzishuai on 2008-03-07
Hi, I am having a problem display a remote X11 window on a ssh server. Then I finally realized the problem may not be network related at all. So I am posting this question here.
Could you please try to run the following in your KDE or any XWin terminal?
```

xterm -display localhost:0.0

```
What I got is
```
xterm Xt error: Can't open display: localhost:0.0
```

I found out that my DISPLAY variable is set to 
```
seki@kalmar mywork $ echo $DISPLAY
:0.0
seki@kalmar mywork $ 
```

So I my display is named without the host name or IP address. I guess that could be the reason I cannot start xterm on a remote host. 

Thank you very much.

PS. I am able to start xterm on all remote Linux/Unix servers except this particular one host. I tried to set the DISPLAY variable manually and run "xhost" on my desktop but it does not help.

---

### Post by jinzishuai on 2008-03-07
After calling a 
```

xhost + localhost

```
I was able to run
```
xterm -display localhost:0.0
```

However, I cannot do the same for the ssh display.

---


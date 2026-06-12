---
title: "Devilspie Problem"
date: 2012-02-19
forum: Desktop Environments
---

### Post by SuperSeijin on 2012-02-19
I have just installed devilspie but having a problem opening web browsers.
I am trying to open multiple browser windows in two different monitors. Each browser has its own web address and are invoked by the windows.open() method in a JavaScript file. The devilspie daemon starts automatically at login.  The problem I am experiencing is after the browsers open they do not get placed as described in the .ds script file.  They just open up in default fashion on the main monitor.  However, when I restart devilspie they go the the predefined coordinates. I want this to be automated, otherwise its just a pain, BTW all other applications work out just fine.

Can someone offer advice?

Here is the code.

Browser #1:   

```
( if 
( and 
( is ( application_name ) "Google Chrome" )
( is ( window_name ) "Table 1 - Google Chrome" )
) 
( begin 
( geometry "944x672+2+357" )
)
)

```

Browser #2:

```
( if 
( and 
( is ( application_name ) "Google Chrome" )
( is ( window_name ) "Table 2 - Google Chrome" )
) 
( begin 
( geometry "944x672+2115+38" )
)
)

```

---


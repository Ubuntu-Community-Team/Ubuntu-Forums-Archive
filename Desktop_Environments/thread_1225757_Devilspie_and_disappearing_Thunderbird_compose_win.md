---
title: "Devilspie and disappearing Thunderbird compose window"
date: 2009-07-28
forum: Desktop Environments
---

### Post by misha680 on 2009-07-28
```

misha@misha-d630:~/Montague Lab/code$ dpkg -l | grep devilspie
ii  devilspie                                  0.21-1                          
                          find windows and perform actions on them

```

Thunderbird and Firefox. Thunderbird by default goes to workspace 1. Firefox to
workspace 2.

Compose in Thunderbird. Move window to workspace 2. Click on Attach. Compose
window disappears but
stays in workstation 2. Simply switch back workspaces to make window appear.

```

[email]misha@misha-d630:~/.devils[/email]pie$ more Firefox.ds 
; generated_rule Firefox
( if 
( and 
( is ( application_name ) "Firefox" )
) 
( begin 
( maximize )
( maximize_vertically )
( maximize_horizontally )
( set_workspace 2 )
( println "match" )
)
)
[email]misha@misha-d630:~/.devils[/email]pie$ more Thunderbird.ds 
; generated_rule Thunderbird
( if 
( and 
( is ( application_name ) "Thunderbird" )
) 
( begin 
( maximize )
( set_workspace 1 )
( maximize_vertically )
( maximize_horizontally )
( println "match" )
)
)

```

[http://bugzilla.gnome.org/show_bug.cgi?id=590097](http://bugzilla.gnome.org/show_bug.cgi?id=590097)

Expected results:
Window not to disappear

Does this happen every time?
Yes

Other information:
Thank you

Anyone else having this problem?

---


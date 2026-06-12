---
title: "gvfsd-http not closing tcp connections"
date: 2011-04-06
forum: Desktop Environments
---

### Post by oscrmyer on 2011-04-06
Everyone knows of the bug in gvfsd-http that leaves connects in close_wait. I say this because I find reports of the bug going back to 2009. :( What I have not found is the fix. Killing the gvfsd-http is the work around. But, what is the fix? 

I find myself asking "W U NO LAST-ACK?"



How to recreate the bug...

Run Rhythmbox, and enable the context pane + album art, and lyrics for good measure as well. Close the plugins windows that pops up, click on the new icon next to the Ubuntu One Music store and your new window should show up. The context pane is great for me, as I love to know what I can about the music I listen to. Rhythmbox, through gvfsd-http has now fetched all your cool text from last.fm about your artist, but it does not close the connection. These connections stay in close_wait till you kill the gvfsd-http process. 

this happens any time gvfsd-http is used. 


netstat -a output 
```

tcp        1      0 farva:47729             10x.terra.com.br:www    CLOSE_WAIT 
tcp        1      0 farva:35961             5b.29.78ae.static.t:www CLOSE_WAIT 
tcp        1      0 farva:36086             5b.29.78ae.static.t:www CLOSE_WAIT 
tcp        1      0 farva:42357             10x.terra.com.br:www    CLOSE_WAIT 
tcp        0      0 farva:47836             64.208.5.34:www         ESTABLISHED
tcp        1      0 farva:42219             10x.terra.com.br:www    CLOSE_WAIT 
tcp        1      0 farva:46945             5b.29.78ae.static.t:www CLOSE_WAIT 
tcp        1      0 farva:36126             5b.29.78ae.static.t:www CLOSE_WAIT 
tcp        1      0 farva:59815             64.208.5.24:www         CLOSE_WAIT 
tcp        0      0 farva:24800             wabothlp0282996.gs:6776 ESTABLISHED
tcp        1      0 farva:36021             5b.29.78ae.static.t:www CLOSE_WAIT 
tcp        0      0 farva:37285             64.208.5.26:www         ESTABLISHED
tcp        1      0 farva:33204             64.208.5.34:www         CLOSE_WAIT 
tcp        1      0 farva:36007             5b.29.78ae.static.t:www CLOSE_WAIT 
tcp        1      0 farva:53431             10x.terra.com.br:www    CLOSE_WAIT 
tcp        1      0 farva:35975             5b.29.78ae.static.t:www CLOSE_WAIT 
tcp        1      0 farva:59027             5b.29.78ae.static.t:www CLOSE_WAIT 
tcp        1      0 farva:47637             10x.terra.com.br:www    CLOSE_WAIT 
tcp        1      0 farva:58324             207.114.197.87:www      CLOSE_WAIT 
tcp     5131      0 farva:42165             10x.terra.com.br:www    CLOSE_WAIT 

```


lsof output.... I am looking at you "can't identify protocol"
```

gvfsd-htt 1795       josh   18r     IPv4              30730      0t0        TCP farva:54963->10x.terra.com.br:www (CLOSE_WAIT)
gvfsd-htt 1795       josh   19u     IPv4              38478      0t0        TCP farva:39645->5b.29.78ae.static.theplanet.com:www (CLOSE_WAIT)
gvfsd-htt 1795       josh   22u     IPv4              23139      0t0        TCP farva:39074->5b.29.78ae.static.theplanet.com:www (CLOSE_WAIT)
gvfsd-htt 1795       josh   24u     IPv4              19766      0t0        TCP farva:42176->10x.terra.com.br:www (CLOSE_WAIT)
gvfsd-htt 1795       josh   25u     sock                0,6      0t0      19650 can't identify protocol
gvfsd-htt 1795       josh   26u     IPv4              19607      0t0        TCP farva:35892->5b.29.78ae.static.theplanet.com:www (CLOSE_WAIT)
gvfsd-htt 1795       josh   27u     IPv4              20164      0t0        TCP farva:42219->10x.terra.com.br:www (CLOSE_WAIT)
gvfsd-htt 1795       josh   29u     IPv4              38494      0t0        TCP farva:51584->10x.terra.com.br:www (CLOSE_WAIT)
gvfsd-htt 1795       josh   30u     sock                0,6      0t0      23195 can't identify protocol
gvfsd-htt 1795       josh   31u     sock                0,6      0t0      20157 can't identify protocol

```

ps -ef |grep 1795 output
```

josh      1795     1  0 14:44 ?        00:00:04 /usr/lib/gvfs/gvfsd-http --spawner :1.11 /org/gtk/gvfs/exec_spaw/3

```

---


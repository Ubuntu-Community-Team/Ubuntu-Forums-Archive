---
title: "wrong epiphany session restoring"
date: 2005-02-21
forum: Desktop Environments
---

### Post by kcs on 2005-02-21
Hi,

I'm using warty, and epiphany. My problem is: if I save my session e.g. with epiphany's windows on 2. desk and log on again (with saved session), epiphany's windows doesn't appear on 2. desk but on 0. desk.
Why doesn't gnome session start it on the right desk?

Thanks
Csaba

in my ~/.gnome2/session file:

11,id=117f000001000110865559700000042390015
11,Program=epiphany-browser
11,CurrentDirectory=/home/kcs
11,DiscardCommand=rm -r /home/kcs/.gnome2/epiphany/session_gnome-svTZJU.xml 
11,CloneCommand=epiphany-browser --sm-config-prefix /epiphany-browser-rzWHS3/ 
11,RestartCommand=epiphany --sm-config-prefix /epiphany-browser-rzWHS3/ --sm-client-id 117f000001000110865559700000042390015 --screen 0 --load-session /home/kcs/.gnome2/epiphany/session_gnome-svTZJU.xml 


from my .metacity/sessions/... file:

 <window id="117f000001000110865559700000042390015" class="Epiphany" name="epiphany" title="search results : vim online" role="" type="normal" stacking="9">
    <workspace index="2"/>
    <geometry x="0" y="25" width="503" height="559" gravity="NorthWestGravity"/>
  </window>


from .gnome2/epiphany/session_gnome-svTZJU.xml :

<window x="0" y="25" width="1043" height="721">
    <embed url="http://www.vim.org/scripts/script_search_results.php?&amp;keywords=python&amp;order_by=rating&amp;show_me=20&amp;result_ptr=20"/>
    <embed url="http://www.google.co.hu/search?hl=hu&amp;q=vim+python&amp;btnG=Keres%C3%A9s&amp;meta="/>
    <embed url="http://www.python.org/doc/current/tut/node8.html"/>
    <embed url="http://www.python.org/doc/current/tut/node11.html"/>
 </window>

---


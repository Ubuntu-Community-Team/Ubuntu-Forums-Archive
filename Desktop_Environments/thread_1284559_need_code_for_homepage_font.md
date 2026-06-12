---
title: "need code for homepage font"
date: 2009-10-06
forum: Desktop Environments
---

### Post by ub9876 on 2009-10-06
here is some code in my prefs file for Google Chrome browser.
My OS is Ubu 9.04.


   "webkit": {
      "webprefs": {
         "default_fixed_font_size": 13,
         "default_font_size": 13,
         "fixed_font_family": "Bitstream Vera Sans Mono",
         "minimum_font_size": 12,
         "minimum_logical_font_siz": 12,
         "sansserif_font_family": "Times New Roman",
         "serif_font_family": "Sans",
         "standard_font_is_serif": false,
         "text_areas_are_resizable": true
      }

can someone recommend some code to make my Google.com homepage
render in 15 size font... and where to put it..
I assume I can put it in with this code above...
Thanks

---

### Post by dummy910 on 2009-10-06
I haven't done this in the Google Browser yet, but based on my knowledge of css and html I would say you would change the following:

*of course always make a backup of any files your editing*

[b]"default_fixed_font_size": [color=red]15[/color],
"default_font_size": [color=red]15[/color],[/b]

and ya might wanna bump the following as well:
[b]"minimum_font_size": [color=red]13[/color],
"minimum_logical_font_siz": [color=red]13[/color],[/b]

---

### Post by ub9876 on 2009-10-06
I changed the code and its staying changed but its still
rendering small...whats the scoop?

---

### Post by dummy910 on 2009-10-06
Did you close the Browser and restart it?

---

### Post by ub9876 on 2009-10-06
yes
maybe its in this code

<!doctype html><html><head><meta http-equiv="content-type" content="text/html; charset=UTF-8"><title>Google</title><script>window.google={kEI:"hfXLSqz8AYjoowTh3cDhBg",kEXPI:"17259,21589,21766,21920,21941,21998,22107,22153",kCSIE:"17259,21589,21766,21920,21941,21998,22107,22153",kCSI:{e:"17259,21589,21766,21920,21941,21998,22107,22153",ei:"hfXLSqz8AYjoowTh3cDhBg"},kHL:"en"};
 
window.google.sn="webhp";window.google.timers={load:{t:{start:(new Date).getTime()}}};try{window.google.pt=window.chrome&&window.chrome.csi&&Math.floor(window.chrome.csi().pageT);
}catch(b){}window.google.jsrt_kill=1;
var _gjwl=location;function _gjuc(){var b=_gjwl.href.indexOf("#");if(b>=0){var a=_gjwl.href.substring(b+1);if(/(^|&)q=/.test(a)&&a.indexOf("#")==-1&&!/(^|&)cad=h($|&)/.test(a)){_gjwl.replace("/search?"+a.replace(/(^|&)fp=[^&]*/g,"")+"&cad=h");return 1}}return 0}function _gjp(){!(window._gjwl.hash&&window._gjuc())&&setTimeout(_gjp,500)};
window._gjp && _gjp()</script><style>td{line-height:.8em;}.gac_m td{line-height:17px;}form{margin-bottom:20px;}body,td,a,p,.h{font-family:arial,sans-serif}.h{color:#36c}.q{color:#00c}.ts td{padding:0}.ts{border-collapse:collapse}em{font-weight:bold;font-style:normal}.lst{font-family:arial,sans-serif;font-size:17px;margin-bottom:0.2em;vertical-align:bottom; }.lsb,.gac_sb{-webkit-appearance:button;padding:0 8px;border:1px solid #999;-webkit-border-radius:2px;background:-webkit-gradient(linear,left top,left bottom,from(#fff),to(#ddd));font-family:arial,sans-serif;font-size:15px;height:1.85em;margin:0.2em;}.lsb:active,.gac_sb:active {background:-webkit-gradient(linear,left top,left bottom,from(#ccc),to(#ddd))}#gbar{float:left;height:22px}.gbh,.gbd{border-top:1px solid #c9d7f1;font-size:1px}.gbh{height:0;position:absolute;top:24px;width:100%}#gbi,#gbg,#gbs,#gbm{background:#fff;left:0;position:absolute;text-align:left;visibility:hidden;z-index:1000}#gbi,#gbg,#gbm{border:1px solid;border-color:#c9d7f1 #36c #36c #a2bae7;z-index:1001}#guser{padding-bottom:7px !important;text-align:right}#gbar,#guser{font-size:13px;padding-top:1px !important}.gb1,.gb3{zoom:1;margin-right:.5em}.gb2{display:block;padding:.2em .5em}a.gb1,a.gb2,a.gb3{color:#00c !important}.gb2,.gb3{text-decoration:none}a.gb2:hover{background:#36c;color:#fff !important}</style><script>google.y={};google.x=function(e,g){google.y[e.id]=[e,g];return false};if(!window.google)window.google={};window.google.crm={};window.google.cri=0;window.clk=function(d,e,f,j,k,l,m){if(document.images){var a=encodeURIComponent||escape,b=new Image,g=window.google.cri++;window.google.crm[g]=b;b.onerror=(b.onload=(b.onabort=function(){delete window.google.crm[g]}));b.src=["/url?sa=T","",e?"&oi="+a(e):"",f?"&cad="+a(f):"","&ct=",a(j||"res"),"&cd=",a(k),d?"&url="+a(d.replace(/#.*/,"")).replace(/\+/g,"%2B"):"","&ei=","hfXLSqz8AYjoowTh3cDhBg",l].join("")}
return true};
window.gbar={qs:function(){},tg:function(e){var o={id:'gbar'};for(i in e)o[i]=e[i];google.x(o,function(){gbar.tg(o)})}};</script></head><body bgcolor=#ffffff text=#000000 link=#0000cc vlink=#551a8b alink=#ff0000 onload="document.f.q.focus();if(document.images)new Image().src='/images/nav_logo7.png'" topmargin=3 marginheight=3><textarea id=csi style=display:none></textarea><iframe name=wgjf style=display:none></iframe><div id=gbar><nobr><b class=gb1>Web</b> <a href="http://images.google.com/imghp?hl=en&tab=wi" onclick=gbar.qs(this) class=gb1>Images</a> <a href="http://video.google.com/?hl=en&tab=wv" onclick=gbar.qs(this) class=gb1>Videos</a> <a href="http://maps.google.com/maps?hl=en&tab=wl" onclick=gbar.qs(this) class=gb1>Maps</a> <a href="http://news.google.com/nwshp?hl=en&tab=wn" onclick=gbar.qs(this) class=gb1>News</a> <a href="http://www.google.com/prdhp?hl=en&tab=wf" onclick=gbar.qs(this) class=gb1>Shopping</a> <a href="http://mail.google.com/mail/?hl=en&tab=wm" class=gb1>Gmail</a> <a href="http://www.google.com/intl/en/options/" onclick="this.blur();gbar.tg(event);return !1" aria-haspopup=true class=gb3><u>more</u> <small>&#9660;</small></a><div id=gbi><a href="http://groups.google.com/grphp?hl=en&tab=wg" onclick=gbar.qs(this) class=gb2>Groups</a> <a href="http://books.google.com/bkshp?hl=en&tab=wp" onclick=gbar.qs(this) class=gb2>Books</a> <a href="http://scholar.google.com/schhp?hl=en&tab=ws" onclick=gbar.qs(this) class=gb2>Scholar</a> <a href="http://www.google.com/finance?hl=en&tab=we" onclick=gbar.qs(this) class=gb2>Finance</a> <a href="http://blogsearch.google.com/?hl=en&tab=wb" onclick=gbar.qs(this) class=gb2>Blogs</a> <div class=gb2><div class=gbd></div></div><a href="http://www.youtube.com/?hl=en&tab=w1" onclick=gbar.qs(this) class=gb2>YouTube</a> <a href="http://www.google.com/calendar/render?hl=en&tab=wc" class=gb2>Calendar</a> <a href="http://picasaweb.google.com/home?hl=en&tab=wq" onclick=gbar.qs(this) class=gb2>Photos</a> <a href="http://docs.google.com/?hl=en&tab=wo" class=gb2>Documents</a> <a href="http://www.google.com/reader/view/?hl=en&tab=wy" class=gb2>Reader</a> <a href="http://sites.google.com/?hl=en&tab=w3" class=gb2>Sites</a> <div class=gb2><div class=gbd></div></div><a href="http://www.google.com/intl/en/options/" class=gb2>even more &raquo;</a> </div></nobr></div><div id=guser width=100%><nobr><b>wb9591@gmail.com</b> | <a href="/url?sa=p&pref=ig&pval=3&q=http://www.google.com/ig%3Fhl%3Den%26source%3Diglk&usg=AFQjCNFA18XPfgb7dKnXfKz7x7g1GDH1tg">iGoogle</a> | <a href="/preferences?hl=en" onclick="this.blur();gbar.tg(event);return !1" aria-haspopup=true aria-owns=gbg class=gb3><u>Settings</u> <small>&#9660;</small></a>| <a href="http://www.google.com/accounts/Logout?continue=http://www.google.com/">Sign out</a><div id=gbg><a href="/preferences?hl=en" class=gb2>Search settings</a> <a href="https://www.google.com/accounts/ManageAccount" class=gb2>Google account settings</a> </div></nobr></div><div class=gbh style=left:0></div><div class=gbh style=right:0></div><center><br clear=all id=lgpd><img alt="Google" height=110 src="/intl/en_ALL/images/logo.gif" width=276 id=logo onload="window.lol&&lol()"><br><br><form action="/search" name=f><table cellpadding=0 cellspacing=0><tr valign=top><td width=25%>&nbsp;</td><td align=center nowrap><input name=hl type=hidden value=en><input name=source type=hidden value=hp><input autocomplete="off" maxlength=2048 name=q size=55 class=lst title="Google Search" value=""><br><input name=btnG type=submit value="Google Search" class=lsb><input name=btnI type=submit value="I'm Feeling Lucky" class=lsb></td><td nowrap width=25% align=left><font size=-2>&nbsp;&nbsp;<a href=/advanced_search?hl=en>Advanced Search</a><br>&nbsp;&nbsp;<a href=/language_tools?hl=en>Language Tools</a></font></td></tr></table></form><br><br><font size=-1><a href="/intl/en/ads/">Advertising&nbsp;Programs</a> - <a href="/services/">Business Solutions</a> - <a href="/intl/en/about.html">About Google</a></font><p><font size=-2>&copy;2009 - <a href="/intl/en/privacy.html">Privacy</a></font></p></center><div id=xjsd></div><div id=xjsi><script>if(google.y)google.y.first=[];if(google.y)google.y.first=[];google.dstr=[];google.rein=[];window.setTimeout(function(){var a=document.createElement("script");a.src="/extern_js/f/CgJlbhICdXMrMAo4PEAILCswDjgHLCswFjgQLCswFzgDLCswGDgELCswGTgLLCswITggQAEsKzAlOMmIASwrMCY4BSwrMCc4AiwrMDw4ACw/TMitWJFqVMc.js";(document.getElementById("xjsd")||document.body).appendChild(a)},0);
;google.y.first.push(function(){google.ac.m=1;google.ac.b=true;google.ac.i(document.f,document.f.q,'','','Q-JZx6oFkNQ4rQEDHsGU7w')});google.xjs&&google.j&&google.j.xi&&google.j.xi()</script></div><script>(function(){
function a(){google.timers.load.t.ol=(new Date).getTime();google.report&&google.report(google.timers.load,google.kCSI)}if(window.addEventListener)window.addEventListener("load",a,false);else if(window.attachEvent)window.attachEvent("onload",a);google.timers.load.t.prt=(new Date).getTime();
})();
</script>(function(){
function a(){google.timers.load.t.ol=(new Date).getTime();google.report&&google.report(google.timers.load,google.kCSI)}if(window.addEventListener)window.addEventListener("load",a,false);else if(window.attachEvent)window.attachEvent("onload",a);google.timers.load.t.prt=(new Date).getTime();
})();
</script>

---

### Post by ub9876 on 2009-10-06
nevermind   got it
it needed to be 15 all the way around   its good now
yee haw

---


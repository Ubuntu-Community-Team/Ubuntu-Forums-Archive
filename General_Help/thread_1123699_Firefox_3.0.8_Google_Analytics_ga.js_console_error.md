---
title: "Firefox 3.0.8 Google Analytics ga.js console errors"
date: 2009-04-12
forum: General Help
---

### Post by nevbear666 on 2009-04-12
Hello everyone

I am having a problem with:
Ubuntu 8.10 (Intrepid Ibex)
Firefox 3.0.8
and the following ga.js call:

<body><script type="text/javascript">
//<![CDATA[
var gaJsHost = (("https:" == document.location.protocol) ? "https://ssl." : "http://www.");
document.write("\<script src='" + gaJsHost + "google-analytics.com/ga.js' type='text/javascript'>\<\/script>" );
//]]>
</script>
<script type="text/javascript">
//<![CDATA[
var pageTracker = _gat._getTracker("UA-########-#");
pageTracker._initData();
//]]>
</script>
...
...
contentdata
...
..
..
<script type="text/javascript">
//<![CDATA[
pageTracker._trackPageview();
//]]>
</script>
</body>

the only script called prior in the head of the page contains:
var browserName=navigator.appName;var browserVer=parseInt(navigator.appVersion);var version="";var msie4=(browserName=="Microsoft Internet Explorer"&&browserVer>=4);if((browserName=="Netscape"&&browserVer>=3)||msie4||browserName=="Konqueror"||browserName=="Opera"){version="n3";}else{version="n2";}
function blurLink(theObject){if(msie4){theObject.blur();}}
function decryptCharcode(n,start,end,offset){n=n+offset;if(offset>0&&n>end){n=start+(n-end-1);}else if(offset<0&&n<start){n=end-(start-n-1);}
return String.fromCharCode(n);}
function decryptString(enc,offset){var dec="";var len=enc.length;for(var i=0;i<len;i++){var n=enc.charCodeAt(i);if(n>=0x2B&&n<=0x3A){dec+=decryptCharcode(n,0x2B,0x3A,offset);}else if(n>=0x40&&n<=0x5A){dec+=decryptCharcode(n,0x40,0x5A,offset);}else if(n>=0x61&&n<=0x7A){dec+=decryptCharcode(n,0x61,0x7A,offset);}else{dec+=enc.charAt(i);}}
return dec;}
function linkTo_UnCryptMailto(s){location.href=decryptString(s,-1);}

on the firefox console i get the following:
1. Warning: reference to undefined property d[_gat.c]
Sourcefile: [http://www.google-analytics.com/ga.js](http://www.google-analytics.com/ga.js)
Line: 2

2. Warning: anonymous function does not always return a value
Sourcefile: [http://www.google-analytics.com/ga.js](http://www.google-analytics.com/ga.js)
Line: 17, Row: 193
Sourcecode:
=A(m);for(r=0;r<b[g];r++){i=b[r];if(f(p,w(i.zb))){m=x(m,"?").join("&");if(f(m,"&"+i.Nb+"=")){u=x(m,"&"+i.Nb+"=")[1];if(f(u,"&"))u=x(u,"&")[0];return new l.n.s(q,i.zb,q,"(organic)","organic",u,q)}}}};k.ba=function(p,u,m){var r=n(p,u+"=","&"),i=!s(r)?

3. Warning: anonymous function does not always return a value
Sourcefile: [http://www.google-analytics.com/ga.js](http://www.google-analytics.com/ga.js)
Line: 18, Row: 134
Sourcecode:
,l.w(p,"/"));if(f(u,"?"))u=x(u,"?")[0];p=x(p,"/")[0]}if(0==l.w(p,"www."))p=l.F(p,4);return new l.n.s(q,p,q,"(referral)","referral",q,u)};k.sc=function(p){var u="";if(k.o.pa){u=l.Db(p);u=""!=u?u+"&":u}u+=p.search;return u};k.zc=function(){return new l.n.s(

It seems that is is the main reason on some pages, why things get rather slow, and not just concerning my own page...

Im not sure if thats a ga problem, or a ubuntu problem, or a firefox problem... if you at least could point me in the right direction, itd be great...

thx for any help
greetings

---


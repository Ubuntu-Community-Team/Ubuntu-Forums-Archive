---
title: "Nagios2 - Wap cgi broken"
date: 2009-06-12
forum: General Help
---

### Post by ezsra.mcdonald on 2009-06-12
I am trying to setup the wap cgi for nagios. Apache sends me the content to download as a file rather than displaying the content.

I have googled for two hours and nothing seems to work. 

The file is not a standard html file. it starts like this:
```

<?xml version="1.0"?>
<!DOCTYPE wml PUBLIC "-//WAPFORUM//DTD WML 1.1//EN" "http://www.wapforum.org/DTD/wml_1.1.xml">
<wml>
<head>
<meta forua="true" http-equiv="Cache-Control" content="max-age=0"/>
</head>
<card id='card1' title='Nagios WAP Interface'>
<p align='center' mode='nowrap'>
<b>Nagios</b><br/><b>WAP Interface</b><br/>
<b><anchor title='Quick Stats'>Quick Stats<go href='statuswml.cgi'><postfield name='style' value='quickstats'/></go></anchor></b><br/>
<b><anchor title='Status Summary'>Status Summary<go href='statuswml.cgi'><postfield name='hostgroup' value='all'/><postfield name='style' value='summary'/></go></anchor></b><br/>
<b><anchor title='Status Overview'>Status Overview<go href='statuswml.cgi'><postfield name='hostgroup' value='all'/><postfield name='style' value='overview'/></go></anchor></b><br/>
<b><anchor title='All Problems'>All Problems<go href='statuswml.cgi'><postfield name='style' value='aprobs'/></go></anchor></b><br/>
<b><anchor title='Unhandled Problems'>Unhandled Problems<go href='statuswml.cgi'><postfield name='style' value='uprobs'/></go></anchor></b><br/>
<b><anchor title='Process Info'>Process Info<go href='statuswml.cgi'><postfield name='style' value='processinfo'/></go></anchor></b><br/>
<b><anchor title='Network Tools'>Tools<go href='#card2'/></anchor></b><br/>
<b><anchor title='About'>About<go href='#card3'/></anchor></b><br/>
</p>
</card>


``` 

the cgi is named statuswml.cgi

Any ideas?

---

### Post by The_Nige on 2009-07-31
Hopefully you have the answer to this by now, but in case you don't...

You are using a browser that does not support WAP, try Opera. I've just started looking at the WAP interface and it seems like you have to login from the front page before you can look at the statuswml.cgi

---


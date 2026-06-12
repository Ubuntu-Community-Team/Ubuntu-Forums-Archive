---
title: "amarok unable to fetch lyrics...."
date: 2009-01-08
forum: General Help
---

### Post by shredder12 on 2009-01-08
I have installed intrepid recently.. and after installing amarok using synaptic i found that i was unable to fetch lyrics..
when i used "lyrc" it gave an error 1 ... with the following details..
```
/usr/lib/ruby/1.8/net/http.rb:560:in `initialize': Connection timed out - connect(2) (Errno::ETIMEDOUT)
	from /usr/lib/ruby/1.8/net/http.rb:560:in `open'
	from /usr/lib/ruby/1.8/net/http.rb:560:in `connect'
	from /usr/lib/ruby/1.8/timeout.rb:53:in `timeout'
	from /usr/lib/ruby/1.8/timeout.rb:93:in `timeout'
	from /usr/lib/ruby/1.8/net/http.rb:560:in `connect'
	from /usr/lib/ruby/1.8/net/http.rb:553:in `do_start'
	from /usr/lib/ruby/1.8/net/http.rb:542:in `start'
	from /usr/lib/ruby/1.8/net/http.rb:1035:in `request'
	from /usr/lib/ruby/1.8/net/http.rb:772:in `get'
	from /usr/share/apps/amarok/scripts/lyrics_lyrc/lyrics_lyrc.rb:127:in `fetchLyrics'
	from /usr/share/apps/amarok/scripts/lyrics_lyrc/lyrics_lyrc.rb:193
	from /usr/share/apps/amarok/scripts/lyrics_lyrc/lyrics_lyrc.rb:179:in `loop'
	from /usr/share/apps/amarok/scripts/lyrics_lyrc/lyrics_lyrc
```

and when i tried to install and run googlelyrics2 it said that it wasn't able to find the lyrics of the track being played..

and when i used wiki-lyrics.. it always shows "fetching lyrics" and nothing shows up for a long time..

Is there is any thing i am missing... 
Well, actually i use a proxy server to access internet.. i have specified it in the network proxy in system->preferences->network proxy and have asked it to be used system wide..
so i don't think that this should be the problem..
Somebody help please...

---

### Post by shredder12 on 2009-01-09
any help please..!!!!

---

### Post by hyper_ch on 2009-01-09
are you using this on amarok2?

---

### Post by shredder12 on 2009-01-09
i don't think so.. i have installed amarok using synaptic.. and there it shows the installed version by the name of "amarok"

---

### Post by hyper_ch on 2009-01-09
well, then it's very likely to be amarok2... where did you get lyrc from?

---

### Post by shredder12 on 2009-01-09
it was already installed with the package..

---

### Post by bswilson on 2009-01-16
I'm having the same problem, **shredder12**.  I have used Amarok on and off for some time, and I just reinstalled it 2 weeks ago.  Ever since this time I have not been able to fetch lyrics via the **lyrc** script.  I receive the same error you're getting.

I'm also using version 1.4.10 from the standard repositories.  I'm sure that's what you're using too.

Additionally, I'm having a weird error with Wikipedia inside Amarok.  I can't pull up any data, I only get this weird language/locale chooser (see attached screen shot).  I don't know what the problem could be; when I click the toolbar button to open the wikipedia page in an external browser, that part works fine.

---

### Post by shredder12 on 2009-01-16
well i think i m having a different issue.. I am unable to guide amarok to internet.
I am in a college and here we use a proxy server.. 
when i clicked on context->artist tab while playing a song... first of all it showed "fetching information from wikipedia" and then after a while it showed "information couldn't be retrieved because the server was unreachable".. so i think there is some problem with the connection settings.. but i m completely clueless..where am i supposed to configure the connection settings in amarok??

---

### Post by bswilson on 2009-01-19
> **shredder12 said:**
> well i think i m having a different issue.. I am unable to guide amarok to internet.
I am in a college and here we use a proxy server.. 
when i clicked on context->artist tab while playing a song... first of all it showed "fetching information from wikipedia" and then after a while it showed "information couldn't be retrieved because the server was unreachable".. so i think there is some problem with the connection settings.. but i m completely clueless..where am i supposed to configure the connection settings in amarok??

Ah yes, that is a different problem.  There's no configuration options *within* Amarok to define a proxy.  There are system-wide settings to do this either for your entire Ubuntu system.

Click on System -> Preferences -> Network Proxy and define your access there, and Amarok should begin working.

---

### Post by shredder12 on 2009-01-19
I have already done that .. but  nothing seems to work..
a weird thing is that while i was looking in amarok configuration i went to Settings->Configure amarok-> engine
and there i saw an option of Http proxy for streaming...strangely this option was already filled with correct proxy settings...
I think this means that some how amarok is being give the right path to the proxy server... but due to some other problem it is not able to download stuff..
Could it be because of the fact that i m running it on gnome.. and so i might not have some useful kde applications installed (which are used for downloading lyrics etc.)..???

---

### Post by woyzeckswoe on 2009-01-19
> **shredder12 said:**
> I have already done that .. but  nothing seems to work..
a weird thing is that while i was looking in amarok configuration i went to Settings->Configure amarok-> engine
and there i saw an option of Http proxy for streaming...strangely this option was already filled with correct proxy settings...
I think this means that some how amarok is being give the right path to the proxy server... but due to some other problem it is not able to download stuff..
Could it be because of the fact that i m running it on gnome.. and so i might not have some useful kde applications installed (which are used for downloading lyrics etc.)..???

i think i've got the same problem,unable to connect to internet im also on gnome...



EDIT i installed kde4:
[http://www.my-guides.net/en/content/view/120/26/](http://www.my-guides.net/en/content/view/120/26/)

and now it works

---

### Post by Helge on 2009-01-22
To set the proxy for Amarok, use Konqueror. At least, that's what I do. Amarok and Konqueror use the same proxy setting. I don't think the Gnome system-wide proxy setting in Ubuntu will affect Amarok.

---

### Post by Helge on 2009-01-22
The weird Wikipedia problem is reported in bug #316140, [https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/316140](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/316140)

---

### Post by shredder12 on 2009-01-22
> **Helge said:**
> The weird Wikipedia problem is reported in bug #316140, [https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/316140](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/316140)

I am not using any different language plugin so, this should not be any problem..

---

### Post by shredder12 on 2009-01-22
> **Helge said:**
> To set the proxy for Amarok, use Konqueror. At least, that's what I do. Amarok and Konqueror use the same proxy setting. I don't think the Gnome system-wide proxy setting in Ubuntu will affect Amarok.

Hey thanks.. Helge you solved my problem.. now i m able to fetch lyrics.. thanks again..

---

### Post by felipebm on 2009-05-06
Hi!
I've just upgraded to Kubuntu Jaunty 9.04 that comes with Amarok2 and I'm able to activate the wikipedia widget but not the lyrics widget.
any idea?
thanks in advance,
Felipe.

---

### Post by middlefinger_to_windows on 2009-11-22
Hi all,

I am using amarok-1.4, and when I try to get the lyrics I am getting this message..

"Lyrics could not be retrieved because the server was not reachable."

Please help..

---

### Post by taryneast on 2010-05-17
> **middlefinger_to_windows said:**
> 
I am using amarok-1.4, and when I try to get the lyrics I am getting this message..

"Lyrics could not be retrieved because the server was not reachable."

Me too. Though I note that if you go directly to lyrc.com it still exists (and is rachable).

Does anyone know if the script have a hard-coded IP address?? If so - will updating that fix it???

---

### Post by ashishbihani on 2012-03-22
i am using ubuntu 11.04. i used kubuntu for around one month in between and the wikipedia plugin, lyrics plugin and cover fetchin plugin were working just fine. these dont work in amarok when i'm using ubuntu. i'm behind a proxy but that should have caused a problem in kubuntu also! please help.

---


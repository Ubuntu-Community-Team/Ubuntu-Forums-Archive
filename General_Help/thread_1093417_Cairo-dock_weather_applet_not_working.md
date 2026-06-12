---
title: "Cairo-dock weather applet not working"
date: 2009-03-11
forum: General Help
---

### Post by J@n on 2009-03-11
Hi All,

So I have been looking around in this forum quite a bit. But I haven't found a solution to my "problem" as yet.

I am running Cairo-Dock 2.0.0-beta 2.1. I am having issues with the weather applet that is provided. I have come to understand that there is a problem with the website the applet looks at. Unfortunately I have not been able to find a single post on how to correct this. I have searched the forum on Cairo-Dock and this forum as well. But I can't find a solution.

As soon as I try to configure the weather applet it tells my it can't find the website and asks me if the connexion (?) is alive.

I am pretty sure it has something to do with the address it looks for information. Alas, I can't find any information on which file to modify to get it working.

Any help is greatly appreciated.

BTW. This problem also occurs in the stable version. So it is not related to the beta.

Greetz,

J@n

---

### Post by chriskin on 2009-03-11
i am using the beta as well, but there is no problem , i get perfect weather for the whole week

are you sure you have configured it correctly?

---

### Post by J@n on 2009-03-11
Hi thanks for your reply.

I have configured the weather applet as stated in the "manual". Right click the applet > Search for your Location > I have put in this: Amsterdam, The Netherlands. The answer: I couldn't get the info. Is connexion alive?

Is there an other way to configure the applet?

Greetz,

J@n

---

### Post by LowSky on 2009-03-11
what about the one built into gnome's calander applet for the top panel? Deos that one have the same issue?

I believe they are all getting there results fromt he same place
Weather.com

By the way its 4'C right now in Amsterdam
[http://www.weather.com/outlook/travel/businesstraveler/local/NLXX0002?from=enhsearch_didyoumean](http://www.weather.com/outlook/travel/businesstraveler/local/NLXX0002?from=enhsearch_didyoumean)

---

### Post by J@n on 2009-03-11
Hi LowSky,

I am not sure about the gnome applet. I haven't tested. I do read in the forum of a number of users having troubles with getting the correct weather forecast with different types of applets. So I think there is a general problem with the connection to the website.

The problem is that I want the weather applet from Cairo-Dock to work and I don't know where to adjust the setting.

Greetz,

J@n

---

### Post by mhgsys on 2009-03-11
@ jan, 

Hey, 
I'm also in Amsterdam, The netherlands. 
lol. 
What you need to do is to get the code, not the name. 
in this case I've got it for you.

Again, right click> configure this applet> Configuration

and put in this at code of your location.: 
FRXX0076

Works fine for me.
mhgsys

---

### Post by J@n on 2009-03-11
Hi Mhgsys,

Nice to know I have a neighbour;-)

Tried FRXX0076 (Doesn't FR stand for France?) but no luck there. Tried different ways but that didn't change anything. I do think it has something to do with the syntax the applet uses. But again, I don't know where to change that.

But if you've got it going so should I be able to get some wheather info out of the applet. So what differs between us? I installed the SVN (1613 I believe) and made no changes in the default configuration. Just tried to add my location. My box is connected to the internet through a router. No ports blocked there. If I go to [www.weather.com](www.weather.com) I can access the site just fine. So WTH is going wrong at my end?

Greetz,

J@n

---

### Post by mhgsys on 2009-03-11
Hey jan 

Lol. about france.. .you're absolulty right:
It has to be NLXX0002

Boy, have I been looking at the wrong weather.
ghehe.

just to know for sure  ,
I did not mean right click > weather > location
but:


right click> configure this applet> Configuration> Code of your location.

and put in NLXX002.

and, btw. Try to open cairo dock in a terminal as root. 
then try to put in the location. (if it works)

and start cairo dock again as user.

---

### Post by fabounet on 2009-03-12
please don't run the dock as root !
it may be a problem of connection timeout
if you have the code, you can try to change the timeout and recompil the applet (be sure to do a make install), then restart the dock to see if it changes something.

---

### Post by mhgsys on 2009-03-12
I only ran the dock as root to change things for the user, not to keep it running as root.
But the first time I installed this dock I was unable as a user to change settings.
That's why I suggested to run as root (temporary)

Why is that such a bad idea?

---

### Post by J@n on 2009-03-12
Well thanks for trying to help me. This is what I did:

Tried running Cairo-dock as root. I am not in the habit of misusing the root account but I had to try;). I started the dock from a terminal and this is the output I got (It got me stumped:()

```
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:290)  
  while opening module '/usr/lib/cairo-dock/libcd-mail.so' : (libgnutls.so.13: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:290)  
  while opening module '/usr/lib/cairo-dock/libcd-xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
OpenGL version: 2.1.2 NVIDIA 177.82
OpenGL vendor: NVIDIA Corporation
OpenGL renderer: GeForce 6100 nForce 405/PCI/SSE2/3DNOW!
warning :  (cairo-dock-config.c:cairo_dock_get_string_key_value:201)  
  Key file does not have key 'depth rotate image'
warning :  (applet-digital.c:cd_clock_configure_digital:34)  
  Attention : No such file or directory
stack : reperoire local : /home/jan/.config/cairo-dock/stack
warning :  (applet-load-icons.c:cd_stack_build_one_icon:54)  
  Stack : Key file does not have key 'Content'
cd_stack_build_one_icon: assertion `cContent != NULL' failed
warning :  (applet-load-icons.c:cd_stack_build_one_icon:54)  
  Stack : Key file does not have key 'Content'
cd_stack_build_one_icon: assertion `cContent != NULL' failed
cairo_dock_check_unique_subdock_name (_Stack_)
n'est pas un directory, menu_path : /
n'est pas un directory, menu_path : /
cairo_dock_search_icon_s_path: assertion `cFileName != NULL' failed
g_pGradationTexture(1) <- 84
g_iIndicatorTexture <- 85
g_iActiveIndicatorTexture <- 86
/tmp/weather-cc.UdCypw:1: parser error : Document is empty

^
/tmp/weather-cc.UdCypw:1: parser error : Start tag expected, '<' not found

^
warning :  (applet-read-data.c:cd_weather_read_data:340)  
  weather : file '/tmp/weather-cc.UdCypw' doesn't exist or is unreadable (no connection ?)
/tmp/weather-forecast.cQa9GW:1: parser error : Document is empty

^
/tmp/weather-forecast.cQa9GW:1: parser error : Start tag expected, '<' not found

^
warning :  (applet-read-data.c:cd_weather_read_data:359)  
  weather : file '/tmp/weather-forecast.cQa9GW' doesn't exist or is unreadable (no connection ?)
window pixmap : 1160x917
window pixmap : 1160x917
8c70320;8586ba0;8d8ec70
iNbConfigDialogs <- 1
cairo_dock_present_group_widget (/home/jan/.config/cairo-dock/current_theme/plug-ins/weather/weather.conf, weather)
on met pLabelContainer:0 (930c9b8 > 930c9b8)
_cairo_dock_find_iter_from_name ()
on met pLabelContainer:945f6e0 (945f6e0 > 94bf2a0)
_cairo_dock_find_iter_from_name (default)
on met pLabelContainer:93c7640 (93c7640 > 94d4b20)
on met pLabelContainer:93c7a98 (93c7a98 > 94d4da0)
on met pLabelContainer:93c92f0 (93c92f0 > 94c48d0)
_cairo_dock_find_iter_from_name (crystal)
_cairo_dock_find_iter_from_name (crystal)
iter:2074167856
ok
_cairo_dock_find_iter_from_name ()
iter:217959111
ok
on_click_apply ()
on_click_ok ()
on_click_apply ()
on_click_quit ()
on_delete_main_gui (0)
iNbConfigDialogs <- 0
/tmp/weather-cc.8i5IXV:1: parser error : Document is empty

^
/tmp/weather-cc.8i5IXV:1: parser error : Start tag expected, '<' not found

^
warning :  (applet-read-data.c:cd_weather_read_data:340)  
  weather : file '/tmp/weather-cc.8i5IXV' doesn't exist or is unreadable (no connection ?)
/tmp/weather-forecast.BjxwJ0:1: parser error : Document is empty

^
/tmp/weather-forecast.BjxwJ0:1: parser error : Start tag expected, '<' not found

^
warning :  (applet-read-data.c:cd_weather_read_data:359)  
  weather : file '/tmp/weather-forecast.BjxwJ0' doesn't exist or is unreadable (no connection ?)
on_click_quit ()
invalid uninstantiatable type `(null)' in cast to `GObject'
g_object_get_data: assertion `G_IS_OBJECT (object)' failed
on_delete_main_gui (0)
iNbConfigDialogs <- 0
gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed
/tmp/weather-cc.Mzkx6a:1: parser error : Document is empty

^
/tmp/weather-cc.Mzkx6a:1: parser error : Start tag expected, '<' not found

^
warning :  (applet-read-data.c:cd_weather_read_data:340)  
  weather : file '/tmp/weather-cc.Mzkx6a' doesn't exist or is unreadable (no connection ?)
/tmp/weather-forecast.ExWzYq:1: parser error : Document is empty

^
/tmp/weather-forecast.ExWzYq:1: parser error : Start tag expected, '<' not found

^
warning :  (applet-read-data.c:cd_weather_read_data:359)  
  weather : file '/tmp/weather-forecast.ExWzYq' doesn't exist or is unreadable (no connection ?)



```

I configured the weather applet as suggested (I found out to use NLXX0002 yesterday;)) but the result is the same. No connection etc.

Then I ran Cairo-dock as a normal user from a terminal. This is the result:

```
jan@Ubuntu:~/Desktop$ cairo-dock
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:290)  
  while opening module '/usr/lib/cairo-dock/libcd-mail.so' : (libgnutls.so.13: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:290)  
  while opening module '/usr/lib/cairo-dock/libcd-xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
OpenGL version: 2.1.2 NVIDIA 177.82
OpenGL vendor: NVIDIA Corporation
OpenGL renderer: GeForce 6100 nForce 405/PCI/SSE2/3DNOW!
warning :  (cairo-dock-config.c:cairo_dock_get_string_key_value:201)  
  Key file does not have key 'depth rotate image'
warning :  (cairo-dock-application-factory.c:cairo_dock_create_surface_from_xpixmap:119)  
  This pixmap is undefined. It can happen for exemple for a window that is in a minimized state when the dock is launching.
warning :  (cairo-dock-application-factory.c:cairo_dock_create_surface_from_xpixmap:119)  
  This pixmap is undefined. It can happen for exemple for a window that is in a minimized state when the dock is launching.
warning :  (applet-digital.c:cd_clock_configure_digital:34)  
  Attention : No such file or directory
stack : reperoire local : /home/jan/.config/cairo-dock/stack
warning :  (applet-load-icons.c:cd_stack_build_one_icon:54)  
  Stack : Key file does not have key 'Content'
cd_stack_build_one_icon: assertion `cContent != NULL' failed
warning :  (applet-load-icons.c:cd_stack_build_one_icon:54)  
  Stack : Key file does not have key 'Content'
cd_stack_build_one_icon: assertion `cContent != NULL' failed
cairo_dock_check_unique_subdock_name (_Stack_)
n'est pas un directory, menu_path : /
n'est pas un directory, menu_path : /
/bin/cp: cannot create regular file `/home/jan/.config/cairo-dock/current_theme/cairo-dock.conf': Permission denied
g_pGradationTexture(1) <- 267
g_iIndicatorTexture <- 268
g_iActiveIndicatorTexture <- 269
```

I am not very good in interpreting the output and therefor don't know if there is a problem to be detected in the output.

I hope this helps.

Greetz,

J@n

---

### Post by fabounet on 2009-03-13
if you run the dock as root, and modify the config, then the config files will then belong to root, which is not what you want.
moreover in general, it's a risk to run any program as root (it can lead to privilege escalation, or a bug can have some serious consequences) 

when you open the themes manager, do you have the [Net] themes ?

---

### Post by angelabrown on 2009-03-15
Hi friend
i know that this is a real problem, but there are many sites that can provide you with the correct weather forecast of Cairo or any other governorate correctly and easily. I know many of these sites one of them is
[http://egyptopia.com/Current+Weather+in+Cairo_51_298_51_en.html]("http://egyptopia.com/Current+Weather+in+Cairo_51_298_51_en.html")
IF you did not find it helpful i can tell you about other better sites too.
Good luck

---

### Post by J@n on 2009-03-15
> **fabounet said:**
> when you open the themes manager, do you have the [Net] themes ?

Hi Fabounet,

No, I cannot find the [Net] themes in the themes manager in Cairo-dock. These are the themes I got:

Wood
Default
Clear
Brit
MacOSX
Neon

Greetz,

J@n

---

### Post by J@n on 2009-03-15
> **angelabrown said:**
> Hi friend
i know that this is a real problem, but there are many sites that can provide you with the correct weather forecast of Cairo or any other governorate correctly and easily. I know many of these sites one of them is
[http://egyptopia.com/Current+Weather+in+Cairo_51_298_51_en.html]("http://egyptopia.com/Current+Weather+in+Cairo_51_298_51_en.html")
IF you did not find it helpful i can tell you about other better sites too.
Good luck

Hi Angelabrown,

I fear you misunderstood my problem. I am not looking for the weather in Cairo but I am trying to get the weather applet supplied with [Cairo-dock]("http://www.cairo-dock.org") up and running.

Thanks for your reply though

---

### Post by mhgsys on 2009-03-15
@j@n, 

I have lot's of theme's in my list. 
Could that be our difference?

Does the weather applet only work with the @ themes?

anyway: 
try

```


sudo apt-get install cairo-dock-plug-ins

```

and try again.

@fabounet
thnx for pointing that out, though I used my root account to change the config of my cairo dock, 
later I gave my user account the same rights, but if I understand correctly  it's not the way it's suppose to go?

---

### Post by J@n on 2009-03-15
Hi Mhgsys,

> Does the weather applet only work with the @ themes?

I am sorry? What do you mean by that:-?

I use the V2 beta. apt-get did not like that very much;) Understandable as I downloaded the deb files and did a manual install (GDebi Package Manager). Anyway....as I reinstalled the deb this is the output I got from the terminal:

[[IMG]http://img264.imageshack.us/img264/4848/terminaloutputreinstall.th.png[/IMG]](http://img264.imageshack.us/my.php?image=terminaloutputreinstall.png)

I will remove and install again. Hope my current config is going to survive that.

Greetz,

J@n

---

### Post by J@n on 2009-03-15
OK. So I removed the plug-ins and reinstalled them again. Installation went fine. I started Cairo-dock from a terminal and checked the weather applet. No change. I used a differnet theme (wood this time) and again checked the weather applet. Nope, still nothing.

This is some of the output from Terminal:
```
/tmp/weather-cc.fUgfY8:1: parser error : Document is empty

^
/tmp/weather-cc.fUgfY8:1: parser error : Start tag expected, '<' not found

^
warning :  (applet-read-data.c:cd_weather_read_data:340)  
  weather : file '/tmp/weather-cc.fUgfY8' doesn't exist or is unreadable (no connection ?)
/tmp/weather-forecast.zF9D62:1: parser error : Document is empty

^
/tmp/weather-forecast.zF9D62:1: parser error : Start tag expected, '<' not found

^
warning :  (applet-read-data.c:cd_weather_read_data:359)  
  weather : file '/tmp/weather-forecast.zF9D62' doesn't exist or is unreadable (no connection ?)
/tmp/weather-cc.GpX77f:1: parser error : Document is empty

^
/tmp/weather-cc.GpX77f:1: parser error : Start tag expected, '<' not found

^
warning :  (applet-read-data.c:cd_weather_read_data:340)  
  weather : file '/tmp/weather-cc.GpX77f' doesn't exist or is unreadable (no connection ?)
/tmp/weather-forecast.i1z2Ey:1: parser error : Document is empty

^
/tmp/weather-forecast.i1z2Ey:1: parser error : Start tag expected, '<' not found

^
warning :  (applet-read-data.c:cd_weather_read_data:359)  
  weather : file '/tmp/weather-forecast.i1z2Ey' doesn't exist or is unreadable (no connection ?)


```

I am thinking of hiring a weatherman to do my forecasting;-)

Greetz,

J@n

---

### Post by mhgsys on 2009-03-15
> Does the weather applet only work with the @ themes?
I am sorry? What do you mean by that


@J@n, 

I ment that I have a list with themes with @ in front of it.
like: @Aero,
But nevermind that I guess, 
I just tried the "wood" theme and my weatherdock seems continu to work,


> 
I use the V2 beta. apt-get did not like that very much Understandable as I downloaded the deb files and did a manual install


Seems to me the easy way out is to start all over again, 
This way has always worked for me, and my weatherdocklet is working like a charme, on all 4 computers here.

[https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)

---

### Post by fabounet on 2009-03-16
aren't you behind a proxy ?
it seems that wget can download the weather page.
if so, you have to set some environment variables (like http_proxy, google it) to help wget.

---

### Post by J@n on 2009-03-16
Hi Guys,

Thanks for your continued interest in my "problem";)

> Seems to me the easy way out is to start all over again, 

I will give it a try later this evening (so much to do so little time;)) But I had this problem also with the latest from the Ubuntu repo (1.6.3)

But as I said: I'll give it a try

> aren't you behind a proxy ?

Nope. No proxy here. I am using a router with NAT and some port forwarding for downloads. That's all. I don't expect any port other than 80 has to be available for the weather applet to get the information.

So to sum it up: I will revert to the stable release tonight and let you know.

Greetz,

J@n

---

### Post by J@n on 2009-03-16
Well...reverted to 1.6.3. Lost most of my customization:( but I can live with that.

Still no working weather applet though. I am kind of lost here. Is there any data that would help analyse the problem? Can I debug Cairo-dock to get more information? If so...how?

Greetz,

J@n

---

### Post by mhgsys on 2009-03-16
lol.


very simple thought:

Do you have firestarter installed?

:you could see if there's anything fom cairo-dock trying to get on the internet.
+
:you should check if it's not blocking it

---

### Post by fabounet on 2009-03-17
try to download something with *wget*.

---

### Post by J@n on 2009-03-17
Hmmm, this is worrying...I tried to ping [www.weather.com](www.weather.com) and this is what happened:

```
jan@Ubuntu:~/Desktop$ ping www.weather.com
PING www.weather.com (65.207.183.121) 56(84) bytes of data.
^C
--- www.weather.com ping statistics ---
131 packets transmitted, 0 received, 100% packet loss, time 130196ms

jan@Ubuntu:~/Desktop$ 

```

So it seems packages are being sent but no response is received. I opened Firestarter but I did not get any useful information. All Outbound traffic is allowed and my router (xxx.yyy.zzz.1) is an allowed connection. I have two custom services that are allowed as inbound on port 16xxx and 22xxx. Is there a specific port I should allow?

And I am sorry for being such a noob but how should I use *wget* to test your suggestion?

Thanks for your continued support=D>

Greetz,

J@n

Edit:

Well I opened port 80 for inbound traffic. And what do you guess? I am getting replies when I ping [www.weather.com](www.weather.com). I do think response times are low but at least I can ping it:

```
jan@Ubuntu:~/Desktop$ ping www.weather.com
PING www.weather.com (63.111.74.121) 56(84) bytes of data.
64 bytes from 63.111.74.121: icmp_seq=1 ttl=244 time=362 ms
64 bytes from 63.111.74.121: icmp_seq=2 ttl=244 time=420 ms
64 bytes from 63.111.74.121: icmp_seq=3 ttl=244 time=264 ms
64 bytes from 63.111.74.121: icmp_seq=4 ttl=244 time=344 ms
64 bytes from 63.111.74.121: icmp_seq=5 ttl=244 time=326 ms
64 bytes from 63.111.74.121: icmp_seq=6 ttl=244 time=360 ms
64 bytes from 63.111.74.121: icmp_seq=7 ttl=244 time=298 ms
^C64 bytes from 63.111.74.121: icmp_seq=8 ttl=244 time=284 ms

--- www.weather.com ping statistics ---
8 packets transmitted, 8 received, 0% packet loss, time 73890ms
rtt min/avg/max/mdev = [COLOR="Red"]264.689/332.697/420.562[/COLOR]/46.989 ms

```

---

### Post by J@n on 2009-03-20
:confused: Anyone?

---

### Post by fabounet on 2009-03-20
did you try to dl something with wget ?

man wget

---

### Post by mhgsys on 2009-03-25
> **J@n said:**
> :confused: Anyone?

hey , 
I was coming back on this because I wondered if you got it to work by now.

about wget, 

for example. 

if you open a terminal 
```

wget www.waarmaarraar.nl

```

this will get you a file called index.html, and is the index.html from that site.

Anyway, What I was curious about, 
When you where able to ping weather.com, did you manage to get the weatherdock running?

+ did you try running the dock with firestarter disabled?
(just open firestarter and press stop firewall)

---

### Post by J@n on 2009-03-25
Hi Mhgsys,

Nope. I did not get the weather applet working as yet. I tried wget as you suggested and that all seemed to be OK.

The output:

```
jan@Ubuntu:~/Desktop$ wget www.waarmaarraar.nl
--2009-03-25 19:41:40--  http://www.waarmaarraar.nl/
Resolving www.waarmaarraar.nl... 85.158.249.226
Connecting to www.waarmaarraar.nl|85.158.249.226|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html'

    [ <=>                                   ] 19,155      --.-K/s   in 0.06s   

2009-03-25 19:41:45 (320 KB/s) - `index.html' saved [19155]

jan@Ubuntu:~/Desktop$ 

```

I disabled Firestarter as you suggested but unluckily that did not provide the solution either. I guess I am stuck with Erwin Krol;)

Any suggestions are still appreciated.

Greetz,

J@n

---

### Post by mhgsys on 2009-03-25
lol. 

Better to have erwin krol then piet paulesma. 
(btw, do a youtube search on piet paulesma winterbanden.. I guess you'll like this commerial.

ontopic:

Did you try to reload the weather after you disabled firestarter???/ when you were able to ping weather.com

I really don't understand why I got it working over here, on all computers, and yours refuses to display the weather/

---

### Post by J@n on 2009-03-26
Hi Mhgsys,

Thanks for your continued support. It is much appreciated :p

I disabled Firestarter and reloaded the weather applet. Without the much hoped for success, I'm sorry to say.

It is not that I can't live without the weather applet (we've got Erwin and Piet;-)), but it annoys me that I can't get it to work properly. Up 'till now I was always able to get things working the way I wanted with the help of this great community (Bill, eat your heart out:))

I am open to any suggestions.

Greetz,

J@n

---

### Post by mhgsys on 2009-03-27
oftopic: 
@ j@n ,  

Well ,fortunately you could also use the weather panel applet.
So you don't _have_ to use cairo-dock for this.

right click your panel> add to panel > weather report 

I actually  got rid of cairo-dock today, I was tired of it using my desktop space, so I found this.

+ I refuse to look at erwin krol or piet paulesma on internet and I banned television few years ago.

btw, it's raining in amsterdam according to the weather applet now. 



:lolflag:

---

### Post by J@n on 2009-03-29
Hi Mhgsys,

As I said: I can live without it but it annoys me that it doesn't work. I am not using Cairo-dock for the weather applet. It was to be a nice bonus. I use it because I like to control my computer through the dock.

I don't use panels anymore because all is accessible through Cairo-dock. And by the way: if you configure it to auto-hide (with short cut) it does not take up any desktop space. As a matter of fact I have more desktop space now 'cause I don't use panels.

Anyway...thanks a million so far. I keep hoping for a solution from the community:)

Greetz,

J@n

---

### Post by mhgsys on 2009-04-08
bump for j@n/

---

### Post by J@n on 2009-04-19
Last attempt:( *Bump*

Anyone?

Greetz,

J@n

---

### Post by J@n on 2009-04-26
Well....progress :)

I just upgraded to Release 2.0.0-rc4 and the weather applet worked immediately.:guitar:

Unfortunately the weather forecast did not get any better ;)

---

### Post by mhgsys on 2009-05-31
@Jan.

:p

lol.

in that case, take a look at the French one .. 
ghehe.

---

### Post by jurjen on 2009-07-12
trying to find out how long it'll be raining, without having to ask our drunk pal piet the weatherman... same problem as j@n, except that upgrading didn't do the trick (just installed a new xubuntu, and thus a new cairo dock from the repos).

but in the config (~/.config/cairo-dock/current_theme/plug-ins/weather/weather.conf) nor in any other location (ie. /usr/share/cairo-dock/.../) I can find any occurrence of a server (such as weather.com) to retrieve the weather data from. Should this be anywhere and if, where? 'Till now it's the only thing I can think of that could be wrong (in my situation at least), my internet connection is fine, no firewall using.

If i find out more i'll let you guys know

---

### Post by TeamJ on 2009-07-12
what's Cairo-dock? sounds good ;D

---

### Post by J@n on 2009-07-13
Hi all,

So that you know...a few days ago I got an update through the repo's. After the update the weather applet ceased to work:(

Ah well... I will wait for the next update to get them fix it again;)

Oh and as a side note: as far as I know the website that is used is hard coded in the applet. I have never been able to find any reference to it from any configuration file. Maybe the website has changed its format thus rendering the applet (momentarily) useless

Fortunately my smartphone shows me the weather (LOL)

Greetz,

J@n

---

### Post by ceciliaFX on 2009-07-14
I have the same situation

I have version 2.0.7

I have read that I need 2.0.8 to fix this problem - I just hope it works with Intrepid 8.10

---

### Post by mdgill on 2009-07-14
One more using V2.0.7 without a working Weather applet.  Shouldn't this be reported as a bug?

---

### Post by mdgill on 2009-07-14
I submitted a bug report here --> [https://bugs.launchpad.net/ubuntu/+source/cairo-dock/+bug/399578](https://bugs.launchpad.net/ubuntu/+source/cairo-dock/+bug/399578)

---

### Post by J@n on 2009-07-15
Hi mdgill,

Just subscribed to your bug report (should have thought of that myself;))

Let's see what happens.

Greetz,

J@n

---

### Post by mdgill on 2009-07-15
Launchpad.net was not the proper place to report a bug for an applet.  Sorry.

Could someone report it here?  --> [http://www.cairo-dock.org/ww_page.php?p=Report%20a%20bug&lang=en](http://www.cairo-dock.org/ww_page.php?p=Report%20a%20bug&lang=en) <--  I am not savy enough to use the debuggers they request.

---

### Post by fabounet on 2009-07-16
wait, we're aware of it already ^_^
and it's been corrected the day after on the SVN.
let us package a version and update the repository :)
if you can't stay qithout this applet anymore, a 2.0.8 is already available on Berlios, but I recommend using the repository.

---

### Post by J@n on 2009-07-17
Hi all,

Just updated and all is working perfectly again. Last update of Cairo-Dock resolved the problem.

Thanks fabounet

Greetz,

J@n

---

### Post by mdgill on 2009-07-17
It is working now for me too along with the SVN-for-dummies explanation here --> [http://www.cairo-dock.org/bg_topic.php?t=3059](http://www.cairo-dock.org/bg_topic.php?t=3059)

---

### Post by seanos on 2009-07-31
Any chance of this update being available for Hardy? 2.0.7 is all that's in the repo.

---

### Post by fabounet on 2009-08-03
yes it will.
sorry for the delay ^_^

---

### Post by seanos on 2009-08-03
Merci!

---

### Post by hihihi on 2009-08-15
upgrading to 2.0.8 did the trick, weather back and running, thanks fabonet, now i go to the beach (zandvoort) haha

---

### Post by fabounet on 2009-08-15
by the way, the package for Hardy is available on Berlios ;-)

---

### Post by ensis2k on 2009-12-07
Sorry to revive this old thread but I have the same problem. Even though my version of cairo is 2.0.9.
[LIST]
[*]**wget [www.weather.com/index.html](www.weather.com/index.html)** works fine.
[*]**ping [www.weather.com](www.weather.com)** does not
[*]**ping [www.google.com](www.google.com)** works
[/LIST]

Is it because I'm behind a proxy? But it shouldnt be a problem because it was working fine just before I reinstalled my system o_O

---

### Post by J@n on 2009-12-07
Hi ensis2K,

I had some problems with earlier versions of 2.x. I upgraded to 2.1.1-2 and now all is working fine. Might be the same for you.

I use this repository (copied from Software Sources dialog):

type: Binary

URI: [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu)

Distribution: karmic

Components: cairo-dock

HTH

Greetz,

J@n

---

### Post by ensis2k on 2009-12-07
Thanks a lot J@n

but the url you have given me is not an apt line. Do I have to compile it myself? I'd like to avoid that if possible.

---

### Post by ensis2k on 2009-12-07
Got it working

For those who end up in the same thread:

Software -> Administration -> software sources -> other software 

Add(for **Ubuntu KARMIC**):
deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) karmic cairo-dock

sudo apt-get update
sudo apt-get upgrade

---

### Post by ronbo191 on 2010-04-29
> **mhgsys said:**
> @ jan, 

Hey, 
I'm also in Amsterdam, The netherlands. 
lol. 
What you need to do is to get the code, not the name. 
in this case I've got it for you.

Again, right click> configure this applet> Configuration

and put in this at code of your location.: 
FRXX0076

Works fine for me.
mhgsys


Sorry to ask such a silly question but where do I get the code for my location? I live in West Haven Connecticut USA.

Never mind. All I had to do was the zip code.

---

### Post by fabounet on 2010-04-29
you can just enter the name of your city and press enter ;)

---

### Post by xtracool_protik on 2010-07-04
fabounet - Entering city name didn't work for me so I went to [www.weather.com](www.weather.com) and put city name there for code and now its working again

---

### Post by J@n on 2011-01-31
Hi All,

I am not in the habit of reviving my own old threads but I am stumped with my favorite applet in cairo-dock (AKA glx-dock), the weather applet. Somehow I appear to have messed up my configuration and the weather applet is not working anymore.

I am running 2.3.0~0beta1 but I have had this issue with all 2.2.x versions.

I have read through this thread and tried all suggestions (again ;)) but this time the weather applet still refuses to show me the weather.

I have tried different locations (NLXX0002 and NLXX0018 ) and different notations (NLxx...., nlxx.... and so forth). Nothing seems to help. I have access to weather.com (through IP and DNS) and I can ping the site. Firestarter is instructed to let the site pass.

As stated in previous (ancient) posts I don't think it is life threatening or I can't live without it but I hate it when I can't get the applet to work properly.

Any tips on how to solve this problem would be much appreciated. As always:)

Greetz,

J@n

---

### Post by J@n on 2011-02-15
Ah well.... not that reviving did any good;)

My problem is miraculously solved. I replaced my router for a new one and apparently I configured some settings over enthusiastic in my old router.

With the basic settings of my new router the weather applet is working again (Huray:))

Greetz,

J@n

---


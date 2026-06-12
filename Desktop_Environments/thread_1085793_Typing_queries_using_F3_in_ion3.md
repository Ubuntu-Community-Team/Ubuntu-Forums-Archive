---
title: "Typing queries using F3 in ion3"
date: 2009-03-03
forum: Desktop Environments
---

### Post by sughosh on 2009-03-03
I have installed ion3 on my ubuntu 8.10 running on my laptop. On starting the session, i am not able to type in queries using the F3 key. The log of .xsession-errors is as follows

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_IN.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
ion3: No encoding given in LC_CTYPE.

But the locale command shows this

sughosh@Hardy:~$ locale
LANG=en_IN
LC_CTYPE=en_IN
LC_NUMERIC="en_IN"
LC_TIME="en_IN"
LC_COLLATE="en_IN"
LC_MONETARY="en_IN"
LC_MESSAGES="en_IN"
LC_PAPER="en_IN"
LC_NAME="en_IN"
LC_ADDRESS="en_IN"
LC_TELEPHONE="en_IN"
LC_MEASUREMENT="en_IN"
LC_IDENTIFICATION="en_IN"
LC_ALL=

Not sure what am i missing out here. Any help would be appreciated. Thanks.

---

### Post by olejorgen on 2009-04-14
> 
thank you all! after the change, things are working just fine.
 
 
On Thu, Apr 9, 2009 at 3:11 PM, Jasbir Khehra <jasbir.k@gmail.com> wrote:
> On Thu, Apr 9, 2009 at 12:29 PM, Tuomo Valkonen <tuomov@iki.fi> wrote:
>> On 2009-04-08, Deepanjan Kesh <deepkesh@gmail.com> wrote:
>>> i have installed ion3 in ubuntu 8.10. but i am not able to type in the
>>> run dialog though tab completion works.
>>> any help would be really appreciated
>>  
>> Fix your locales settings. You need the .encoding (e.g. fi_FI.UTF-8)
>> part in LC_CTYPE (or LANG), because Xlib is broken.
> Hi Deepanjan,
> To change the locales setting you need to modify /etc/default/locales
> and reboot.
> Check the output with locale command.
>  

Maybe this will help?

---


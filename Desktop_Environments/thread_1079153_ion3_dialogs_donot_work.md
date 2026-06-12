---
title: "ion3 dialogs donot work"
date: 2009-02-24
forum: Desktop Environments
---

### Post by spider_jerusalem on 2009-02-24
Recently installed ion3 (20070207-2 hardy). Cannot enter text in none of the ion3 dialogs. Eg: f3 opens "run.." dialog - I can tab-complete but cannot enter any text. Any help would be great ...

---

### Post by olejorgen on 2009-04-14
> thank you all! after the change, things are working just fine.
 
 
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

Maybe?

---


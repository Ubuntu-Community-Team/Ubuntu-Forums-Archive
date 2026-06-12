---
title: "Evolution: filter problem"
date: 2008-12-13
forum: General Help
---

### Post by litlfrog on 2008-12-13
I've set up a rule in Evolution that's not working correctly. It's pretty simple, and I can't figure out where else to look for the problem. The rule has only one criterion and one action. The criterion is

Subject
contains
keep active

The action is 

Move to folder
Inbox/KeepActive.

The folder exists and works fine; I can drag messages into it with no problem. The filter's just not moving anything there. I get a lot of messages every day to keep accounts active (this is a business e-mail address) that I just never need to refer to, so I want them to stop cluttering my inbox and automatically go in to this separate folder I've created. I've tried using

keep active
keep AND active
"keep active"

and none of them seem to make the filter do anything. Anyone have insight here?

---

### Post by rbmorse on 2008-12-13
Sort of a longshot, but folder names are case sensitive, so if the storage folder name is:  

KeepActive

and your filter is set up to send the file to a folder named 

keepactive

it probably won't work.

---

### Post by litlfrog on 2008-12-14
OK, if I change the filter to 

> Subject
contains
active 

instead of 

> Subject 
contains
keep active

then the filter works. Can that box only contain one search term?

---


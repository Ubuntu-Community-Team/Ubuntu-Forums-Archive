---
title: "Conky- top and top_mem"
date: 2009-06-13
forum: Desktop Environments
---

### Post by blur xc on 2009-06-13
Could someone explain do me what he difference is between the top and top_mem variable in conky?  Especailly since both can display cpu% and mem%, and why I should have them in my conky?

I'm finally picking up steam in uderstanding how it all works- Here's my screenshot so far.  Bear in mind it's a work in progress- I take that back...  when I browse to find a file to upload, it doens't show any files in my pictures folder...

BM

---

### Post by b.a.w on 2009-06-13
top gives you the top processes based on cpu usage. top_mem gives you the process ranked by memory usage. Taking a line from my .conkyrc

```
${top name 1}   ${top pid 1}    ${top cpu 1}
```This gives the number one process name ranked by cpu usage, the pid of that process, and its cpu usage.

```
${top_mem name 1}  ${top_mem pid 1}    ${top_mem mem 1}
```

Using top_mem, this gives the number one process ranked by memory usage, the pid of that process, and the percent memory usage.

It is also valid to use {top mem 1}. This gives the memory usage of the top cpu process. The same goes for {top_mem cpu 1}.

---

### Post by blur xc on 2009-06-13
Thanks, seems to make a little sense.  I just confusing to me since both top and top mem have cpu and mem percentages, at least from the .conkyrc that I saved and have been hacking.  Here's what I ahve so far.  My desktop has a ways to go, but so far I'm liking the conky.  I'm considering adding some up/down transfer information and calling it good, though once I settle on a theme and background, I'll most likely have to adjust the colors.

Thanks again,
BM

---


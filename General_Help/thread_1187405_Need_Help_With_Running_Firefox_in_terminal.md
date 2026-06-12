---
title: "Need Help With Running Firefox in terminal"
date: 2009-06-14
forum: General Help
---

### Post by alibahaloo on 2009-06-14
im a geek in linux system, so help me :)
when i try to run firfox from terminal, this happens:

```

alibahaloo@DELL:~$ firefox
/home/alibahaloo/.themes/Tigris-Globalmenu/gtk-2.0/gtkrc:75: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/alibahaloo/.themes/Tigris-Globalmenu/gtk-2.0/gtkrc:122: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/alibahaloo/.themes/Tigris-Globalmenu/gtk-2.0/gtkrc:178: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/alibahaloo/.themes/Tigris-Globalmenu/gtk-2.0/gtkrc:231: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
Loading stream: http://talkgadget.google.com/talkgadget/resources/chatsound.swf
unhandled event 19
^C
alibahaloo@DELL:~$ 
```

what are these lines? and why the terminal wont let me to type more commands unless i press ctrl+C to and if i do that the firefox shuts down?

thanks 

Ali.B

---

### Post by Yeti can't ski on 2009-06-23
Hi! You probably mean that you are a "rookie" and not a "geek", right? Geek usually means very nerd, skilled and proficient! :)

Anyway, in spite of those error messages you are able to open and use Firefox, aren't you?

It is normal to have such error messages. In your case, it seems to be simply a warning of the fact that a specific color scheme of Firefox will be discontinued in the future.

As per why you cannot continue to type in terminal, it is because the terminal is busy with the process (that is, with running Firefox). 

You can always open a new terminal window to do other things or make "Ctrl+Z", instead of "Ctrl+C", to send the process to the background. That means that Firefox will keep operative but you can use the terminal. 

You can make Firefox start from the background from the very beginning with the symbol "&", that is, with the following command: 

firefox &

Another alternative is to switch to another virtual console, but that is much more messy. In any event, please note that if you close the terminal window Firefox will shut down. 

I hope to have been of assistance. 

Good luck and best regards!

---


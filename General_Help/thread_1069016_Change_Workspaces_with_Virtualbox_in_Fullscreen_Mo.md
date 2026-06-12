---
title: "Change Workspaces with Virtualbox in Fullscreen Mode"
date: 2009-02-13
forum: General Help
---

### Post by jnewm on 2009-02-13
Hi all,

I wanted to be able to change workspaces with Virtualbox in fullscreen mode, without pressing the right control key to uncapture my keyboard.  I found hints about how to do this through various Google searches, and finally pieced it together.  So I thought I'd do a quick post in case anyone else has this goal.

#1 - Start by reading the great instructions here about changing keyboard shortcuts: [http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/).  

#2 - But you can skip the keybinding_command steps and go straight to global_keybindings, because you'll already find commands for "switch_to_workspace_right," "switch_to_workspace_left," and other workspace changing commands.

#3 For the desired global_keybinding change the value to "Scroll_Lock" or "Pause".  (Do not put <> around these values, type them exactly as written, without the quotes.  I think Scroll_Lock and Pause work because Virtualbox does not capture them (at least to Windows XP).  There may be other keys that Virtualbox does not capture.  I didn't play around too much.

Personally, I assigned "Scroll_Lock" to "switch_to_workspace_left" and "Pause" to "switch_to_workspace_right", since Scroll_Lock is on the left and Pause is on the right on my keyboard.  So switching workspaces for me is easy and intuitive.

And that's it!  Switch workspaces with Virtualbox in fullscreen mode without having to uncapture the keyboard.  I know, this isn't a very impressive trick, but it took me a bit to figure it out, and I thought maybe I'd save someone a little time :).  And I LOVE, when I need to use Windows for something: to have it already running fullscreen on my far left workspace; to just press Scroll_Lock to get there; and to just press a single Pause key to shift back to the right and my Ubuntu workspaces.

PS That reminds me, I need to get to work, so no more posts.  But if anyone wants, I also figured out how (through great advice from another post), at least on my computer, to hibernate with Virtualbox running.  So, when I start my computer back up, I don't have to boot Windows back up in Virtualbox (which is huge for me, since it takes forever).

---


---
title: "Startup with fav apps on different workspaces [Solution]"
date: 2008-08-28
forum: Desktop Environments
---

### Post by Wickd on 2008-08-28
Hi there!

I have found a very simple way of launching your favorite applications such as skype, mail and music all on different workspaces/viewports

Here we go:

1) Install Devilspie 
        - *sudo aptitude install devilspie*

2) Set up directory for Devilspace
        - *mkdir ~/.devilspie*

3) Set up the Rules. This is where a little programming knowledge comes in handy, but I will give you a basic code structure that you can use:

        i) cd ~/.devilspie
       ii) sudo gedit skype.ds (This will open the text editor)
      iii) Put the following code into the editor:

              [B](if
              (matches (application_name) "Skype")
              (begin
              (set_workspace 2)
              )
              )[/B]

           The number value after the *set_workspace* is the desired worksapce 
           number starting from 1

       iv) Save and close the editor. [I]Please note that if you are
           using the cube effect for linux. You are using one
           workspace with differnet viewports!! So change
           "set_workspace" to "set_viewport" with the desired number.[/I]

4) Now go to System > Preferences > Sessions and under the
   Startup Programs add the following two ***seperate*** programs: 
  1) devilspie
  2) Skype
   in the command lines.

5) Log out and back in. If you log back in, skype should open in your
   desired viewport/workspace

For more actions and parameters please visit [http://foosel.org/linux/devilspie#comment__03c2be11c8f4ca9bb09945dfe8a1ea3d]("http://foosel.org/linux/devilspie#comment__03c2be11c8f4ca9bb09945dfe8a1ea3d")

---

### Post by hakimaki on 2008-08-28
Always wanted to do something like this.  Will try when I get home from work.

---


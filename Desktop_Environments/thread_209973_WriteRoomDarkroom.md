---
title: "WriteRoom/Darkroom/?"
date: 2006-07-06
forum: Desktop Environments
---

### Post by dicesquirrel on 2006-07-06
Hello everyone, long time listener, first time poster. ;)

My problem is this: I was reading Lifehacker.com, and they suggested a Windows app called "Darkroom," a clone of the OS X program "WriteRoom." 

[http://www.hogbaysoftware.com/product/writeroom](http://www.hogbaysoftware.com/product/writeroom)

Basically, I really really want this simple functionality, and I haven't been able to find it via any text editor for Linux. Does anyone have some suggestions? I need these features:
- Fullscreen, no window border
- Green text, Courier New, 12 pt
- Ability to pad the text on either side, creating a column like WriteRoom does, for ease of reading, while not interfering terribly with the formatting.
- Easily save to .txt, preferably with a nice key combination like ctrl-s
- No title line or formatting lines like nano/pico
- Not totally necessary, but it would really help: word-wrap!

I've tried out vim, found it way too complex and byzantine for my simple purposes. I tried using Abiword with a black background, green text, in F11 fullscreen mode, but that retained a menu bar and window border. I suppose if I could get rid of the menu bar I could live with the menu bar.

Thanks for your time.

---

### Post by atoponce on 2006-07-06
You need to get familiar with Vim.  Although the learning curve may be steep initially, it is one of those skills that you'll be glad you learned.

Using the Gnome terminal, I can have 100% full screen (no menu, no borders, no nothing) just by pressing F11.  I can change the color of the text as I please, I can easily save to text files and many many more features that you want plus more.

Launching vim in screen, I then can have access to the document remotely either via SSH or Telnet plus being able to edit and create locally. Vim and Gnome terminal are by far your best bet.

---

### Post by dicesquirrel on 2006-07-06
I had a sinking suspicion that was true, heh. vim does indeed seem very powerful, and I will delve into it.

Could you offer any tips on how I can achieve what I'm going for, though? Perhaps a nice tutorial that you might recommend?

So far I've got these elements in vim:
- Fullscreen, no window border
- Green text, Courier New, 12 pt

I need:
- Ability to pad the text on either side, creating a column like WriteRoom does, for ease of reading, while not interfering terribly with the formatting.
- Easily save to .txt, preferably with a nice key combination like ctrl-s
          [I know how to save, but is there a key combination or macro I could use? Or perhaps some script that saves as I type, much like WriteRoom?]
- Word-wrap
- for those blue tildes that start every line to disappear. Call me crazy, but it's just more visual clutter that I'd rather not have. Any way to do this?

I will certainly RTFM, but as TFM is right next to a phonebook in size, it'll be a while, and I'd appreciate any help you veterans can give. :)

Thanks again!

---

### Post by ryorininseven on 2006-07-06
I've actually been trying to find a similar program, myself. I would write one if I wasn't so lazy and so used to vim's functionality. :p

What I've been doing:

1) Run VIM fullscreen. Not even gvim, unless that's what you'd prefer.

2) :set wiw=90

3) :vsplit

Do that last one twice. You'll end up with three frames. Select the center one, then hit [ Ctrl ][ = ]. Voila! Centered, 90-character wide window. Unfortunately, it's not too elegant.

Alternatively, if you've got gvim compiled with Motif or Xaw/Athena support instead of GTK2, you can define the window padding just like any other Xaw application, but that'll pad all sides of the window rather than just the left and right. That is, unless there's some way to pad specific sides. I forget.

---

### Post by ryorininseven on 2006-07-07
Okay, I lied about being lazy. I'm working on a (very) rudimentary text editor based off of ncurses --- at the moment, it's basically a pretty way to do `cat >> filename.txt << EOF`.

[[IMG]http://fileanchor.com/42124-t.png[/IMG]](http://fileanchor.com/42124.png)

It works more or less like a typewriter. To set it up like in the picture, it's just a fullscreen urxvt:

urxvt -sb -b 25 -fg green -bg black -fn "xft:Courier 10 Point:size=10:antialias=true" -e ped

If anybody wants to give it a try, reply here or send me a PM.

---

### Post by atoponce on 2006-07-08
> **ryorininseven said:**
> Okay, I lied about being lazy. I'm working on a (very) rudimentary text editor based off of ncurses --- at the moment, it's basically a pretty way to do `cat >> filename.txt << EOF`.

[[IMG]http://fileanchor.com/42124-t.png[/IMG]]("http://fileanchor.com/42124.png")

It works more or less like a typewriter. To set it up like in the picture, it's just a fullscreen urxvt:

urxvt -sb -b 25 -fg green -bg black -fn "xft:Courier 10 Point:size=10:antialias=true" -e ped

If anybody wants to give it a try, reply here or send me a PM. Not bad.  Looks really good.  What are you coding it in?

---

### Post by ryorininseven on 2006-07-08
C++. I'm a little rusty after having spent a year dealing with Java, but it works, and quickly.

---

### Post by soze on 2006-07-08
You can do this with emacs:

You will need the wmctrl package:

```
sudo apt-get install wmctrl
```

Put the following in your ~/.emacs file:

```
(defun darkroom-mode ()
        (interactive)

        (shell-command "wmctrl -r darkroom -badd,fullscreen")

        (set-background-color "black")
        (set-foreground-color "green")

        (set-cursor-color "white")
        (setq left-margin 10)
        (menu-bar-mode -1)
        (tool-bar-mode -1)
        (scroll-bar-mode -1)
        (transient-mark-mode 1)


        (set-face-foreground 'region "black")
        (set-face-background 'region "green")

        (set-face-foreground 'mode-line "gray15")
        (set-face-background 'mode-line "black")

        (move-to-left-margin 0 1)
        (auto-fill-mode)
        (setq text-mode-hook 'darkroom-mode)

)

```

launch it with:

```
emacs -f darkroom-mode  -title darkroom -fn -adobe-courier-medium-r-normal--25-180-100-100-m-150-iso8859-1 foo.txt
```

where foo.txt is the name of the file you want to edit (you probably want to alias this)

Enjoy!

---

### Post by ryorininseven on 2006-07-08
Ooh. Sweet deal.

---

### Post by dicesquirrel on 2006-07-10
With the gracious help of one of my friends, Arek the Absolute on GameDev.net, I now have a solution to my problems!

Even better than that, I have the source, and I've been tweaking it (with his considerable help) to be even better with each iteration. Hopefully someday it will be ready for primetime in Universe or something!

Create a new directory and navigate to it:
```
mkdir aedit
cd aedit
```

Open up a new file with gedit:
```
gedit main.cpp
```

Paste this text into the gedit window:
```
/*
This program is free software; you can redistribute it and/or
modify it under the terms of the GNU General Public License
as published by the Free Software Foundation; either version 2
of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program; if not, write to the Free Software
Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA  02111-1307, USA.
*/

/*
    This program is simply a sensory-deprivation themed text editor, for concentration purposes.
    CTRL+SHIFT+BACKSPACE quits, CTRL+SHIFT+S saves. The first line is used as the filename.
    Compile with -DSCROLL option to enable a vertical scrollbar.
*/

#include <gtk/gtk.h>
#include <gdk/gdkkeysyms.h>
#include <iostream>
#include <fstream>
#include <string>
using namespace std;

void Destroy();
gboolean Accel(GtkAccelGroup *accel_group, GObject *acceleratable, guint keyval, GdkModifierType modifier);
void modify_cursor_color(GtkWidget *widget, GdkColor *color);

GtkWindow *window = NULL;
GtkWidget *scroll = NULL;
GtkWidget *edit = NULL;

/* the main program is given as a DLL when compiled for Windows to allow the main program to locate the GTK
   runtimes before executing the program itself. This is irrelevant to any other platform. */
#ifdef _WIN32
#include <windows.h>
extern "C" __declspec(dllexport) int Main(int argc, char *argv[]){
#else
int main(int argc, char *argv[]){
#endif

    gtk_init(&argc,&argv);

    // create the window
    window = (GtkWindow*)gtk_window_new(GTK_WINDOW_TOPLEVEL);
    gtk_window_fullscreen(window);
    gtk_window_set_title(window,"Editor");
    gtk_window_set_keep_above(window,true);
    gtk_widget_set_size_request(GTK_WIDGET(window),600,400);
    g_signal_connect(window,"delete_event",G_CALLBACK(Destroy),NULL);
    edit = gtk_text_view_new();
    //set the side margins for maximum readability
    gtk_text_view_set_left_margin(GTK_TEXT_VIEW(edit),256);
    gtk_text_view_set_right_margin(GTK_TEXT_VIEW(edit),256);
    gtk_widget_set_name(edit,"GtkEditorView");
    gtk_text_view_set_wrap_mode(GTK_TEXT_VIEW(edit),GTK_WRAP_WORD);
    scroll = gtk_scrolled_window_new(NULL,NULL);

    // simply add a scroll window to allow for convenient scrolling capabilities like the mouse wheel
    gtk_container_add(GTK_CONTAINER(window),scroll);
    ((GtkScrolledWindow*)scroll)->hscrollbar_policy = GTK_POLICY_NEVER;
#ifdef SCROLL
    ((GtkScrolledWindow*)scroll)->vscrollbar_policy = GTK_POLICY_AUTOMATIC;
#else
    ((GtkScrolledWindow*)scroll)->vscrollbar_policy = GTK_POLICY_NEVER;
#endif
    gtk_container_add(GTK_CONTAINER(scroll),edit);

    GdkColor color;
    gdk_color_parse("black",&color);
    gtk_widget_modify_base(edit,GTK_STATE_NORMAL,&color);

    gdk_color_parse("green",&color);
    gtk_widget_modify_text(edit,GTK_STATE_NORMAL,&color);

    gdk_color_parse("yellow",&color);
    modify_cursor_color(edit,&color);

    // set the font to monospace
    GtkTextBuffer *buffer = gtk_text_view_get_buffer(GTK_TEXT_VIEW(edit));
    PangoFontDescription *font_desc = pango_font_description_from_string("Courier New,Monospace 12");
    gtk_widget_modify_font(edit,font_desc);
    pango_font_description_free(font_desc);

    // if specified in the command prompt, attempt to open a file
    if (argc > 1){
        ifstream file(argv[1]);
        if (file){

            // prepend the file name on its own line for saving purposes
            string body = argv[1];
            body.append("\n");
            while (file && file.peek() != EOF) body += file.get();
            gtk_text_buffer_set_text(buffer,body.c_str(),body.length());
        }
    } else {
        // if no file is specified, simply provide a quick introduction
        string intro =  "filename.txt\n\n"
                "CTRL+SHIFT+BACKSPACE to quit (without saving)\n"
                "CTRL+SHIFT+S to save (first line is used as filename)\n";
        //Comment the next line if you don't want the initial text shown.
	gtk_text_buffer_set_text(buffer,intro.c_str(),intro.length());
    }

    GtkAccelGroup *accel = gtk_accel_group_new();
    GClosure *closure;
    GdkModifierType CTRL_SHIFT = (GdkModifierType)(GDK_CONTROL_MASK | GDK_SHIFT_MASK);

    // add the quit shortcut
    closure = g_cclosure_new(G_CALLBACK(Accel),NULL,NULL);
    gtk_accel_group_connect(accel,GDK_BackSpace,CTRL_SHIFT,(GtkAccelFlags)0,closure);

    // add the save shortcut
    closure = g_cclosure_new(G_CALLBACK(Accel),NULL,NULL);
    gtk_accel_group_connect(accel,GDK_S,CTRL_SHIFT,(GtkAccelFlags)0,closure);

    gtk_window_add_accel_group(window,accel);
    gtk_widget_show_all(GTK_WIDGET(window));

    // enter the main application loop
    gtk_main();

    return 0;
}

void Destroy(){
    gtk_main_quit();
}

gboolean Accel(GtkAccelGroup *accel_group, GObject *acceleratable, guint keyval, GdkModifierType modifier){
    if (keyval == GDK_BackSpace)
        Destroy();
    else if (keyval == GDK_S || keyval == GDK_s){
        GtkTextIter start, end;
        GtkTextBuffer *buffer = gtk_text_view_get_buffer(GTK_TEXT_VIEW(edit));
        gtk_text_buffer_get_start_iter(buffer,&start);
        gtk_text_buffer_get_iter_at_line(buffer,&end,1);
        gchar *line = gtk_text_buffer_get_slice(buffer,&start,&end,false);
        if (!line) return true;

        if (line[0]){
            for (int i = 0; line[i] != 0; i++){
                if (line[i] == '\b' || line[i] == '\r' || line[i] == '\n') line[i] = 0;
            }
            ofstream file(line);
            start = end;
            gtk_text_buffer_get_end_iter(buffer,&end);
            gchar *body = gtk_text_buffer_get_slice(buffer,&start,&end,false);
            file << body;
            g_free(body);
            file.close();
        }

        g_free(line);
    }
    return true;
}

/*
Thanks to gedit source:
A hack to change the cursor color (widget must be named!)
*/
void modify_cursor_color(GtkWidget *widget, GdkColor *color){
    static const char cursor_color_rc[] =
        "style \"editor\"\n"
        "{\n"
            "GtkTextView::cursor-color=\"#%04x%04x%04x\"\n"
        "}\n"
        "widget \"*.%s\" style : application \"editor\"\n";

    const gchar *name;
    gchar *rc_temp;

    name = gtk_widget_get_name(widget);
    if (!name) return;

    if (color){

        rc_temp = g_strdup_printf(cursor_color_rc,
                color->red,
                color->green,
                color->blue,
                name);

    } else {
        GtkRcStyle *rc_style;

        rc_style = gtk_widget_get_modifier_style(widget);

        rc_temp = g_strdup_printf(cursor_color_rc,
                rc_style->text[GTK_STATE_NORMAL].red,
                rc_style->text[GTK_STATE_NORMAL].green,
                rc_style->text[GTK_STATE_NORMAL].blue,
                name);
    }

    gtk_rc_parse_string(rc_temp);
    gtk_widget_reset_rc_styles(widget);

    g_free(rc_temp);
}

```

Save it and exit gedit. Now, back in the terminal, enter:
```
g++ -o editor main.cpp `pkg-config --cflags gtk+-2.0` `pkg-config --libs gtk+-2.0`
```

Run the program:
```
./editor
```

It's sloppy, it could probably be done better, and could stand to have a few more features. Arek and I would love to hear any suggestions you have. Also, if anyone has any suggestions on how to pad the margins out based on number of characters in the column rather than an arbitrary number of pixels, we'd love to hear it, that's one tangle we've yet to work out.

Thanks!

---

### Post by jonrkc on 2006-07-10
Rapidly scanning these posts, I didn't see anybody suggest nedit.

Nedit is very customizable and might be able to do all you require; it seems very useful for programming purposes though I don't use it that way.  

Worth looking into, anyway.

---

### Post by dicesquirrel on 2006-07-10
I wanted this program just so I could get rid of all the distractions that come with having a sweet, sweet, Ubuntu-running computer connected to the intarwebs, and write a damn paper from time to time without interruptions.

For this purpose, I consider it damn near perfect. For coding? Awful. :D

---

### Post by soze on 2006-07-10
I really don't see the point to creating a new editor from scratch for this purpose.

The emacs-based solution I presented above takes care of your requirements, plus you have all of emacs at your disposal (spell check, etc.)

I don't think re-inventing the wheel is necessary for something as simple as this.

---

### Post by pete on 2006-07-11
> **dicesquirrel said:**
> I wanted this program just so I could get rid of all the distractions that come with having a sweet, sweet, Ubuntu-running computer connected to the intarwebs, and write a damn paper from time to time without interruptions.

For this purpose, I consider it damn near perfect. For coding? Awful. :D

dicesquirrel--  I agree, this is great.  Nice and simple, w/no distractions.  Thanks!:D

---

### Post by gwilma on 2006-07-13
If you want a simple way to do it, why no try gedit with the toolbar, statusbar and sidebar all turned off. I've just modified the example plugin for it slightly, to include a "Toggle fullscreen" button in the View menu. To have a go with it, get the package from [http://live.gnome.org/data/Gedit(2f)Plugins/attachments/fullscreen-2006-07-13.tar.bz2]("http://live.gnome.org/data/Gedit(2f)Plugins/attachments/fullscreen-2006-07-13.tar.bz2")

And extract it to ~/.gnome2/gedit/plugins (make the directory if you don't have it already). Then restart gedit, go to Edit>Preferences, click on the plugins button, and tick the checkbox next to "Fullscreen plugin" to get it working.

As gedit plugins etc get submitted, I'm starting to like it more and more.

---

### Post by Scraplab on 2006-08-09
I love what you've done dicesquirrel. Would be great to have a quit prompt, but aside from that, I'd say it's feature complete!

---

### Post by Kerim on 2007-01-17
Had the same problem.
Since i have no mac, Writeroom was out of question.
Darkroom seemed nice but i hate installing .NET just because of one application AND it would run only under windows.
I wanted to learn python anyway so i thought i just reinvent the wheel.
Slowly but steadily gaining functionality. (redo, undo this week hopefully)

[http://codeboje.de/blog/archives/Matrix-updated.html](http://codeboje.de/blog/archives/Matrix-updated.html)

Didn't test it under Linux yet. I just installed virtual box today and will put Ubuntu 6.10 on the vm tomorrow hopefully.

BTW: The emacs solution sounds good.

---

### Post by hugmenot on 2007-02-09
I agree with the motivation to have distracting elements removed.
My preferred editor is vim so not much to do to emulate the appearance of this thing.
The cheap hack is using two vsplits and having the lateral windows empty¹.
I modded the colorschemes darktango and rdark a little and using metacity gvim goes fullscreen on keypress

If only the irony weren&#8217;t that doing this was again procrastination. You always find a way ...


¹Which can still be useful to quickly look at stuff, or hold a project tree.

²BTW you can run vim in a mode that emulates a simple editor (with Ctrl-C, Ctrl-V, mouse selection, and the like).

---

### Post by Karl S. on 2007-03-07
Have you looked here, at [Writer]("http://writer.bighugelabs.com/")?

---

### Post by NoWhereMan on 2007-06-24
[http://www.codealchemists.com/jdarkroom/](http://www.codealchemists.com/jdarkroom/)

btw I would use vim (i'd just want a ...clean... way to pad the left and right margins to make it look nicer ;)) and scribes is very good as well
hugmenot, what's the font you're using in your terminal/gvim ?

---

### Post by pgmario on 2007-06-24
Wow, this aedit thing is cool, thanks a lot!

---

### Post by timmie on 2007-07-26
Me too, I like this aedit thing.

Maybe you would like to put the code somewhere on a page like Launchpad or Sourceforge.

Then it can get packaged, extended etc...

---

### Post by ryorininseven on 2007-08-21
Hey, I hate to engage in thread necromancy, but I ended up dropping my first *room project and recently began putzing with a pre-existing lightweight text editor. I'm putting the finishing touches on a heavily modified Leafpad; I call it a4e (A4 editor, previously Leafpad A4). I've attached a screenshot of what it looks like.

So yeah -- the features so far:

- User-configurable text color/background color/font (Ctrl-comma, Ctrl-period, Ctrl-slash)
- Save/Open through standard dialogs (Ctrl-S, Ctrl-O)
- Search/Replace (Ctrl-F, Ctrl-R, Ctrl-N/P for next/previous)
- Fullscreen
- Prettified text spacing for readability (probably configurable in the future)

Which is to say, most of those were Leafpad features. I removed the menu, then added in the configurable colors, fullscreen, and text formatting stuff.

(EDIT: Bar added. Refer to [Q10](http://www.baara.com/q10/) for the inspiration.)

I actually drew most of the edits from aedit, so props to Dicesquirrel and Arek the Absolute. You guys saved me from a headache or two.

Same code requirements as Leafpad -- namely, libgtk2.0-dev. Just run the usual stuff: ./configure && make && make install.

Ninja edit: I noticed a typo in my demo.txt file, so I changed it for the screenshot. I was too lazy to repack/reupload the .tar.gz, though. :p

Not Nina edit: Come to think of it -- if anybody versed in GTK can tell me how to add padding to a GtkTextView widget or keep the cursor in the middle row of the screen, I would appreciate the help *immensely*. I'm not sure if I like how the text runs into the bottom of the window like that.

Further edit: It took me all of a few minutes to add the search stuff back in. Woo!

**Mega Ultra Edit**
I think this is pretty much what I want to do with the program. There are, again, a few more tweaks -- but it's effectively complete.

**I should stop editing**
Note that there's sometimes lag when trying to use the mouse to highlight text. I don't know why this happens, because sometimes it will work fine and other times it will lag like crazy.

**But I keep editing anyway**
Okay, I figured it out. For reasons beyond my understanding, running A4 from a terminal will result in normal mouse behavior. Running it from, say, a Beryl shortcut will make it all laggy. What?

---

### Post by NoWhereMan on 2007-08-26
ouch! does this mean I'm on late? :D

btw, your app looks nice... here my first attempt at pygtk, hope you'll like it; it looks almost like write/darkroom; in the very first lines you can find some vars you can customize for colors, font, etc...

of course like 'aedit' is GPL'd ;)

shortcuts:

Ctrl-O : open
Ctrl-S : save (or save as if not saved)
Ctrl-Shift-S : Save as
Ctrl-Q : quit

files are NOT autosaved; you people may want to add such a feature, take it, it's yours :)

bye!

**pyroom.py**
```

#!/usr/bin/env python

#pyroom.py

import pygtk
pygtk.require('2.0')
import gtk
import gobject
import pango

class PyRoomStatus (gtk.Label):

	timeout = 2000

	def set_timeout(self, time):
		self.timeout = time

	def blank(self):
		self.set_text('')
		return False

	def push(self, text):
		self.set_text(text)
		gobject.timeout_add(self.timeout, self.blank)
	
	def put(self, text):
		self.set_text(text)



	
class PyRoom:
	
	BORDER = 40
	SIDEMARGIN = 256
	BGCOLOR = 'black'
	FGCOLOR = 'green'
	FONT = 'DejaVu Sans Mono 14'
	current_file = None

	def delete_event(self, widget, event, data=None):
		return False

	def destroy(self, widget, data=None):
		# self.save_file(None, None, None, None)
		gtk.main_quit()

	def __init__(self):
		# create a new window
		self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
		self.window.fullscreen()
	
		self.window.connect("delete_event", self.delete_event)
		self.window.connect("destroy", self.destroy)


		self.window.modify_bg(gtk.STATE_NORMAL, gtk.gdk.color_parse(self.BGCOLOR))

	
		# New TextView
		self.textbox = gtk.TextView()

		# With green cursor
		gtk.rc_parse_string("""
		style "pyroom-colored-cursor" {
			GtkTextView::cursor-color = '""" +
				self.FGCOLOR
			+ """'
		}
		class "GtkWidget" style "pyroom-colored-cursor"
		""")


		self.textbox.modify_base(gtk.STATE_NORMAL, gtk.gdk.color_parse(self.BGCOLOR))
		self.textbox.modify_text(gtk.STATE_NORMAL, gtk.gdk.color_parse(self.FGCOLOR))
		self.textbox.set_wrap_mode(gtk.WRAP_WORD)
		self.textbox.modify_font(pango.FontDescription(self.FONT))
		

		self.fixed = gtk.Fixed()
	
		self.vbox = gtk.VBox()

		
		height = gtk.gdk.screen_height()
		width = gtk.gdk.screen_width() - 2*self.SIDEMARGIN

		self.window.add(self.fixed)

		self.fixed.put(self.vbox, self.SIDEMARGIN, 0)
		self.vbox.set_size_request(height, width)

		self.scrolled = gtk.ScrolledWindow()

		self.vbox.pack_start(self.scrolled, True, True, self.BORDER)
		self.scrolled.add(self.textbox)
		self.scrolled.set_policy(gtk.POLICY_NEVER, gtk.POLICY_NEVER)
		self.scrolled.show()

		self.scrolled.set_property("resize-mode", gtk.RESIZE_PARENT)
		self.textbox.set_property("resize-mode", gtk.RESIZE_PARENT)
		self.vbox.set_property("resize-mode", gtk.RESIZE_PARENT)
	
		self.textbox.show()
		self.vbox.show()
		
		self.status = PyRoomStatus()
		lbl = self.status 

		self.vbox.pack_end(lbl, False, False, 0)

		lbl.modify_fg(gtk.STATE_NORMAL, gtk.gdk.color_parse(self.FGCOLOR))
		lbl.modify_font(pango.FontDescription(self.FONT))
		
		lbl.set_justify(gtk.JUSTIFY_LEFT)
		lbl.show()


		self.setup_actions()


		self.fixed.show()
		self.window.show()

		self.status.push('Welcome to PyRoom')


	def setup_actions(self):
		self.accels = gtk.AccelGroup()
		self.accels.connect_group(ord('Q'), gtk.gdk.CONTROL_MASK, 0, self.quit)
		self.accels.connect_group(ord('S'), gtk.gdk.CONTROL_MASK, 0, self.save_file)
		self.accels.connect_group(ord('S'), 
				gtk.gdk.CONTROL_MASK | gtk.gdk.SHIFT_MASK, 0, self.save_file_as)
		self.accels.connect_group(ord('O'), gtk.gdk.CONTROL_MASK, 0, self.open_file)
		self.window.add_accel_group(self.accels)

	def quit(self, accel_group, acceleratable, keyval, modifier):
		gtk.main_quit()

	def open_file(self, accel_group, acceleratable, keyval, modifier):
		chooser = gtk.FileChooserDialog(
				'PyRoom',
				None,
				gtk.FILE_CHOOSER_ACTION_OPEN,
				buttons=(
					gtk.STOCK_CANCEL,
					gtk.RESPONSE_CANCEL,
					gtk.STOCK_OPEN,
					gtk.RESPONSE_OK
					)
				)
		chooser.set_default_response(gtk.RESPONSE_OK)

		res = chooser.run()
		if res == gtk.RESPONSE_OK:       
			self.current_file = chooser.get_filename()
			chooser.destroy()
			f=open(self.current_file, 'r')
			buff = gtk.TextBuffer()
			buff.set_text(f.read())
			buff.place_cursor(buff.get_start_iter())
			self.textbox.set_buffer(buff)
			f.close()
			self.status.push('File ' + self.current_file + ' open')
			return
	
		chooser.destroy()
		self.status.push( 'Closed, no files selected' )
 


	def save_file(self, accel_group, acceleratable, keyval, modifier):
		if self.current_file:
			f=open(self.current_file, 'w')
			buff = self.textbox.get_buffer()
			txt = buff.get_text(buff.get_start_iter(), buff.get_end_iter())
			f.write(txt)
			f.close()
			self.status.push('File ' + self.current_file + ' saved')
		else:
			self.save_file_as(accel_group, acceleratable, keyval, modifier)	

	def save_file_as(self, accel_group, acceleratable, keyval, modifier):
		chooser = gtk.FileChooserDialog(
				'PyRoom',
				None,
				gtk.FILE_CHOOSER_ACTION_SAVE,
				buttons=(
					gtk.STOCK_CANCEL,
					gtk.RESPONSE_CANCEL,
					gtk.STOCK_SAVE,
					gtk.RESPONSE_OK
					)
				)
		chooser.set_default_response(gtk.RESPONSE_OK)
		res = chooser.run()
		if res == gtk.RESPONSE_OK:       
			self.current_file = chooser.get_filename()
			chooser.destroy()
			self.save_file(accel_group, acceleratable, keyval, modifier)   
			return

		self.status.push( 'Closed, no files selected' )
		chooser.destroy()


 


	def main(self):
		gtk.main()

if __name__ == "__main__":
	pyroom = PyRoom()
	pyroom.main()

```

---

### Post by robog2 on 2007-08-26
ryorininseven: Just installed your a4e beta, and I have a problem.  The fullscreen seems to be offset by a bit (does not cover the whole screen), and there appears to be no word wrap (text continues on the same line forever).  

I also cannot find a way to remove the program (would love to keep it if those issues are solved).  

Otherwise, the program seems very good and would be a perfect substitue for Darkroom or Writeroom.

Thanks

---

### Post by NoWhereMan on 2007-08-26
looks neat!

about the padding thing, I've used a fixed container, so I had just to put the textarea on a given x,y with fixed w,h;

as it is fullscreen, fixed width,height, x, y are not a great deal, once you know the screensize :), this let you NOT use the margin property, which othwerwise makes  your cursor an 'insert-text' even out of the actual editable area :)

 BTW, I can't see the bar at the bottom, because the size *of the main window* is somehow fixed to a too large value of width... ok, smaaaall patch (commented out one thing and moved around another pair)

attaching the file :)

PS: as a suggestion (if you have time/will), no "save file? " questions, but autosave, auto-re-open last file, and autosave every n min/secs

bye!

---

### Post by robog2 on 2007-08-26
Thanks for the patch NoWhereMan.  Fullscreen now works for me.  But I don't understand why the right margin does not work correctly (despite the explanation).  Any way to fix it?

Thanks again.

---

### Post by ryorininseven on 2007-08-26
> **robog2 said:**
> ryorininseven: Just installed your a4e beta, and I have a problem.  The fullscreen seems to be offset by a bit (does not cover the whole screen), and there appears to be no word wrap (text continues on the same line forever).  

I also cannot find a way to remove the program (would love to keep it if those issues are solved).  

Otherwise, the program seems very good and would be a perfect substitue for Darkroom or Writeroom.

Thanks

Looks like whatever window manager you're using is forcing decorations on the application, or keeping it out of fullscreen mode; by default, it requests fullscreen and the entire width/height of the display. That'd also explain why the bar is invisible.

Also, make sure you're running the latest version, found here:

[http://ryorinin.betterwebber.com/a4e-beta3.tar.gz](http://ryorinin.betterwebber.com/a4e-beta3.tar.gz)

I don't have either of those issues, but it might be a window manager thing. Beryl on Feisty handles it with no problem.

EDIT: Wait, I see NoWhereMan patched it. Wehey!

If you want to remove a4e, just do

sudo rm /usr/local/bin/a4e

I never bothered to test whether 'make uninstall' worked. Sorry about that. :) I'll look into the automatic saving and file recovery stuff tomorrow when I get the chance.

EDIT TWO: I implemented NoWhereMan's patch and found out the highlighting delay is apparently Beryl-specific? Interesting. Works like a charm in normal X.

---

### Post by robog2 on 2007-08-26
I tried "make uninstall" again and it worked!  Must have had a bad install before.  Any ideas about the margin issue (or are you even having the same issue)?

I'm not having the highlighting issue in X either by the way (must be Beryl).

Thanks

---

### Post by ryorininseven on 2007-08-26
The highlighting issue is definitely Beryl; I just confirmed it by running a4e in Metacity. Works like a charm, there. As for the margin -- I'm not having that problem. Weird. I mean, the screenshot I posted was of a freshly compiled installation; unless there's some flag getting messed up, text should be wrapped properly. In fact, GTK_WRAP_WORD is set explicitly every time the program is run. It *will* continue forever if you type in a stream of characters with no whitespace, though.

Come to think of it -- what version of Ubuntu and GCC/GTK are you using to compile this?

---

### Post by robog2 on 2007-08-27
Wow... I didn't even think to type words.  I held down a single key, which was the problem.  No word wrap issues after all.  How dumb of me.  Thanks!

By the way... is there any way to adjust the column width?  

Thanks again for the help!

---

### Post by zeta on 2007-09-03
Hi there,
this looks like a very promising app. Thanks a lot!
Some minor things though: I have the same problem with the a4e not beeing full screen, it is a bit off to the bottom. Yes I installed the newest version. I tried to apply the patch, but I have no idea how to do it? :confused: (Agreed, this is not the noob-section of the forum, but plLLLLEASE help me with this)
Plus: Would it be possible to have the cursor not going lower than center like in WriteRoom? This is actually the feature I am looking for the most. When I'm writing a longer piece, it is SO annoying to stare all the time at the bottom of the screen. ...and a small row-/word-counter would be nice.:)

---

### Post by ryorininseven on 2007-09-03
No way to adjust the text column size -- yet. It's an easy tweak. I resume classes tomorrow, but the workload should taper off by the weekend. I'll make a few additions then.

The patch posted by NoWhereMan fixed the fullscreen problems. Easiest way to add it in: slap his main.c into a4e's src/ directory (overwriting the old one) and rebuild. The patch will be integrated with the next version, though, so look for that this weekend.

As for keeping the cursor only halfway down the screen: I'm working on it. I don't like typing while staring at the lower edge of the screen either. ;) Word counts and whatnot might be a little trickier, but I'll see what I can do.

---

### Post by zeta on 2007-09-04
Great...and thanks a lot! :)

---

### Post by robog2 on 2007-09-04
Awesome.  Can't wait!

---

### Post by Phayder92889 on 2007-09-05
As an aspiring writer, this is a fantastic tool for a distraction-free workspace. Thanks so much for taking the time to code something like this, ryorininseven, thanks for patching, NowhereMan.

Is there a word count thing in the bar at the bottom, or is that coming later?

---

### Post by zeta on 2007-09-05
Great. I just applied the patch and it works! Thanks again ryorininseven and NoWhereMan (sounds like a broken clock now, but I am really happy about this app):)

Regarding the word/row-counter: I would be just as happy with an optional row-counter (for every five rows or so) to the left of the text, just like in a normal editor.

---

### Post by a-dub on 2007-10-16
there's always CTRL-ALT-F1, login, vim/pico/etc, CTRL-ALT-F7

---

### Post by NoWhereMan on 2007-10-16
but i like that text-column effect :)

---

### Post by bennyp on 2007-10-28
I've tried a4e and it's quite nice. It would be amazing to see some more options like custom colours, or perhaps having that bottom bar auto-hide as a menu bar. That would be snazzy, and a very welcome novelty from the usual menu at top configuration.

Nice Work.

---

### Post by Phayder92889 on 2007-11-05
It's not fullscreening for me anymore. it's working just fine, but it has a border, and I'm not pleased with its border-having-ness...

help?

---

### Post by dedmonds on 2007-11-09
I use vim (fullscreen [F11], as mentioned) in the GNOME terminal with a special larger-sized green text on black profile specifically for writing. (I'm also a vim addict, so take that for what it's worth.)

- Duane

---

### Post by corneliuscrab on 2007-11-12
Here's another native Linux editor I found recently:

[http://rubyroom.rubyforge.org/](http://rubyroom.rubyforge.org/)

Requires ruby-gnome2

I also just got the Q10 portable app version working with the latest Wine packages from winehq (had trouble with the default Gutsy packages) ... yeah I know, but it's got some really nice features, and can run off a USB stick.

---

### Post by bagofchickens on 2007-11-13
Ryorininseven, a4e is great. Please consider adding scrolling by mouse wheel and some statistics such as paragraph, line and characters with spaces count. Yesterday I saw Q10 for the first time and it got me so envious I thought I was going to burst in flames :) Particularly the way you can define your own page count rules, as well as the ability to use OpenOffice dictionaries for spell check.

The Emacs trick also works quite well. I had some issues with PyRoom and Gyounen, but maybe it was just on my end.

---

### Post by tryscer on 2007-11-16
I hope I don't sound like a complete idiot, but I can't seem to make a4e install. I get the configure part okay, but when trying to "make", it spews this long long message. Any idea why this is?

---

### Post by tryscer on 2007-11-18
...eh. To be more specific, here's the installation log.

> This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

It was created by a4e configure 0.8.9, which was
generated by GNU Autoconf 2.61.  Invocation command line was

  $ ./configure 

## --------- ##
## Platform. ##
## --------- ##

hostname = tryscer-laptop
uname -m = i686
uname -r = 2.6.22-14-generic
uname -s = Linux
uname -v = #1 SMP Sun Oct 14 23:05:12 GMT 2007

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = unknown
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
/usr/bin/hostinfo      = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/local/sbin
PATH: /usr/local/bin
PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin
PATH: /usr/games


## ----------- ##
## Core tests. ##
## ----------- ##

configure:1843: checking for a BSD-compatible install
configure:1899: result: /usr/bin/install -c
configure:1910: checking whether build environment is sane
configure:1953: result: yes
configure:2018: checking for gawk
configure:2048: result: no
configure:2018: checking for mawk
configure:2034: found /usr/bin/mawk
configure:2045: result: mawk
configure:2056: checking whether make sets $(MAKE)
configure:2077: result: yes
configure:2276: checking for style of include used by make
configure:2304: result: GNU
configure:2377: checking for gcc
configure:2393: found /usr/bin/gcc
configure:2404: result: gcc
configure:2642: checking for C compiler version
configure:2649: gcc --version >&5
gcc (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:2652: $? = 0
configure:2659: gcc -v >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.1.3 --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
configure:2662: $? = 0
configure:2669: gcc -V >&5
gcc: '-V' option must have argument
configure:2672: $? = 1
configure:2695: checking for C compiler default output file name
configure:2722: gcc    conftest.c  >&5
configure:2725: $? = 0
configure:2763: result: a.out
configure:2780: checking whether the C compiler works
configure:2790: ./a.out
configure:2793: $? = 0
configure:2810: result: yes
configure:2817: checking whether we are cross compiling
configure:2819: result: no
configure:2822: checking for suffix of executables
configure:2829: gcc -o conftest    conftest.c  >&5
configure:2832: $? = 0
configure:2856: result: 
configure:2862: checking for suffix of object files
configure:2888: gcc -c   conftest.c >&5
configure:2891: $? = 0
configure:2914: result: o
configure:2918: checking whether we are using the GNU C compiler
configure:2947: gcc -c   conftest.c >&5
configure:2953: $? = 0
configure:2970: result: yes
configure:2975: checking whether gcc accepts -g
configure:3005: gcc -c -g  conftest.c >&5
configure:3011: $? = 0
configure:3110: result: yes
configure:3127: checking for gcc option to accept ISO C89
configure:3201: gcc  -c -g -O2  conftest.c >&5
configure:3207: $? = 0
configure:3230: result: none needed
configure:3250: checking dependency style of gcc
configure:3340: result: gcc3
configure:3433: checking for perl
configure:3451: found /usr/bin/perl
configure:3463: result: /usr/bin/perl
configure:3496: checking for iconv
configure:3514: found /usr/bin/iconv
configure:3527: result: /usr/bin/iconv
configure:3537: checking for msgfmt
configure:3568: result: msgfmt
configure:3578: checking for msgmerge
configure:3609: result: msgmerge
configure:3619: checking for xgettext
configure:3650: result: xgettext
configure:3687: gcc -o conftest -g -O2   conftest.c  >&5
configure:3693: $? = 0
configure:3860: checking for gcc
configure:3887: result: gcc
configure:4125: checking for C compiler version
configure:4132: gcc --version >&5
gcc (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:4135: $? = 0
configure:4142: gcc -v >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.1.3 --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
configure:4145: $? = 0
configure:4152: gcc -V >&5
gcc: '-V' option must have argument
configure:4155: $? = 1
configure:4158: checking whether we are using the GNU C compiler
configure:4210: result: yes
configure:4215: checking whether gcc accepts -g
configure:4350: result: yes
configure:4367: checking for gcc option to accept ISO C89
configure:4470: result: none needed
configure:4490: checking dependency style of gcc
configure:4580: result: gcc3
configure:4623: checking for pkg-config
configure:4641: found /usr/bin/pkg-config
configure:4654: result: /usr/bin/pkg-config
configure:4676: checking for GTK+ - version >= 2.0.0
configure:4832: result: no
configure:4870: gcc -o conftest -g -O2 -Wall    conftest.c   >&5
conftest.c:11:21: error: gtk/gtk.h: No such file or directory
conftest.c: In function 'main':
conftest.c:17: error: 'gtk_major_version' undeclared (first use in this function)
conftest.c:17: error: (Each undeclared identifier is reported only once
conftest.c:17: error: for each function it appears in.)
conftest.c:17: error: 'gtk_minor_version' undeclared (first use in this function)
conftest.c:17: error: 'gtk_micro_version' undeclared (first use in this function)
configure:4876: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "a4e"
| #define PACKAGE_TARNAME "a4e"
| #define PACKAGE_VERSION "0.8.9"
| #define PACKAGE_STRING "a4e 0.8.9"
| #define PACKAGE_BUGREPORT "tarot@sdf.lonestar.org"
| #define PACKAGE "a4e"
| #define VERSION "0.8.9"
| /* end confdefs.h.  */
| 
| #include <gtk/gtk.h>
| #include <stdio.h>
| 
| int
| main ()
| {
|  return ((gtk_major_version) || (gtk_minor_version) || (gtk_micro_version));
|   ;
|   return 0;
| }
configure:5043: checking pkg-config is at least version 0.9.0
configure:5046: result: yes
configure:5057: checking for GNOMEPRINT
configure:5065: $PKG_CONFIG --exists --print-errors "libgnomeprintui-2.2"
Package libgnomeprintui-2.2 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libgnomeprintui-2.2.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libgnomeprintui-2.2' found
configure:5068: $? = 1
configure:5083: $PKG_CONFIG --exists --print-errors "libgnomeprintui-2.2"
Package libgnomeprintui-2.2 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libgnomeprintui-2.2.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libgnomeprintui-2.2' found
configure:5086: $? = 1
No package 'libgnomeprintui-2.2' found
configure:5114: result: no
configure:5155: checking how to run the C preprocessor
configure:5195: gcc -E  conftest.c
configure:5201: $? = 0
configure:5232: gcc -E  conftest.c
conftest.c:10:28: error: ac_nonexistent.h: No such file or directory
configure:5238: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "a4e"
| #define PACKAGE_TARNAME "a4e"
| #define PACKAGE_VERSION "0.8.9"
| #define PACKAGE_STRING "a4e 0.8.9"
| #define PACKAGE_BUGREPORT "tarot@sdf.lonestar.org"
| #define PACKAGE "a4e"
| #define VERSION "0.8.9"
| /* end confdefs.h.  */
| #include <ac_nonexistent.h>
configure:5271: result: gcc -E
configure:5300: gcc -E  conftest.c
configure:5306: $? = 0
configure:5337: gcc -E  conftest.c
conftest.c:10:28: error: ac_nonexistent.h: No such file or directory
configure:5343: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "a4e"
| #define PACKAGE_TARNAME "a4e"
| #define PACKAGE_VERSION "0.8.9"
| #define PACKAGE_STRING "a4e 0.8.9"
| #define PACKAGE_BUGREPORT "tarot@sdf.lonestar.org"
| #define PACKAGE "a4e"
| #define VERSION "0.8.9"
| /* end confdefs.h.  */
| #include <ac_nonexistent.h>
configure:5381: checking for grep that handles long lines and -e
configure:5455: result: /bin/grep
configure:5460: checking for egrep
configure:5538: result: /bin/grep -E
configure:5543: checking for ANSI C header files
configure:5573: gcc -c -g -O2 -Wall  conftest.c >&5
configure:5579: $? = 0
configure:5678: gcc -o conftest -g -O2 -Wall   conftest.c  >&5
configure:5681: $? = 0
configure:5687: ./conftest
configure:5690: $? = 0
configure:5707: result: yes
configure:5731: checking for sys/types.h
configure:5752: gcc -c -g -O2 -Wall  conftest.c >&5
configure:5758: $? = 0
configure:5774: result: yes
configure:5731: checking for sys/stat.h
configure:5752: gcc -c -g -O2 -Wall  conftest.c >&5
configure:5758: $? = 0
configure:5774: result: yes
configure:5731: checking for stdlib.h
configure:5752: gcc -c -g -O2 -Wall  conftest.c >&5
configure:5758: $? = 0
configure:5774: result: yes
configure:5731: checking for string.h
configure:5752: gcc -c -g -O2 -Wall  conftest.c >&5
configure:5758: $? = 0
configure:5774: result: yes
configure:5731: checking for memory.h
configure:5752: gcc -c -g -O2 -Wall  conftest.c >&5
configure:5758: $? = 0
configure:5774: result: yes
configure:5731: checking for strings.h
configure:5752: gcc -c -g -O2 -Wall  conftest.c >&5
configure:5758: $? = 0
configure:5774: result: yes
configure:5731: checking for inttypes.h
configure:5752: gcc -c -g -O2 -Wall  conftest.c >&5
configure:5758: $? = 0
configure:5774: result: yes
configure:5731: checking for stdint.h
configure:5752: gcc -c -g -O2 -Wall  conftest.c >&5
configure:5758: $? = 0
configure:5774: result: yes
configure:5731: checking for unistd.h
configure:5752: gcc -c -g -O2 -Wall  conftest.c >&5
configure:5758: $? = 0
configure:5774: result: yes
configure:5792: checking build system type
configure:5810: result: i686-pc-linux-gnu
configure:5832: checking host system type
configure:5847: result: i686-pc-linux-gnu
configure:5885: checking locale.h usability
configure:5902: gcc -c -g -O2 -Wall  conftest.c >&5
configure:5908: $? = 0
configure:5922: result: yes
configure:5926: checking locale.h presence
configure:5941: gcc -E  conftest.c
configure:5947: $? = 0
configure:5961: result: yes
configure:5994: checking for locale.h
configure:6002: result: yes
configure:6016: checking for LC_MESSAGES
configure:6042: gcc -o conftest -g -O2 -Wall   conftest.c  >&5
configure:6048: $? = 0
configure:6065: result: yes
configure:6094: checking libintl.h usability
configure:6111: gcc -c -g -O2 -Wall  conftest.c >&5
configure:6117: $? = 0
configure:6131: result: yes
configure:6135: checking libintl.h presence
configure:6150: gcc -E  conftest.c
configure:6156: $? = 0
configure:6170: result: yes
configure:6203: checking for libintl.h
configure:6210: result: yes
configure:6221: checking for ngettext in libc
configure:6249: gcc -o conftest -g -O2 -Wall   conftest.c  >&5
configure:6255: $? = 0
configure:6273: result: yes
configure:6277: checking for dgettext in libc
configure:6305: gcc -o conftest -g -O2 -Wall   conftest.c  >&5
configure:6311: $? = 0
configure:6329: result: yes
configure:6338: checking for bind_textdomain_codeset
configure:6394: gcc -o conftest -g -O2 -Wall   conftest.c  >&5
configure:6400: $? = 0
configure:6418: result: yes
configure:6905: checking for msgfmt
configure:6935: result: no
configure:7543: creating ./config.status

## ---------------------- ##
## Running config.status. ##
## ---------------------- ##

This file was extended by a4e config.status 0.8.9, which was
generated by GNU Autoconf 2.61.  Invocation command line was

  CONFIG_FILES    = 
  CONFIG_HEADERS  = 
  CONFIG_LINKS    = 
  CONFIG_COMMANDS = 
  $ ./config.status 

on tryscer-laptop

config.status:704: creating Makefile
config.status:704: creating src/Makefile
config.status:704: creating po/Makefile.in
config.status:839: WARNING:  po/Makefile.in.in seems to ignore the --datarootdir setting
config.status:704: creating config.h
config.status:975: executing depfiles commands
config.status:975: executing intltool commands
config.status:975: executing default-1 commands
config.status:975: executing po/stamp-it commands

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_build=i686-pc-linux-gnu
ac_cv_c_compiler_gnu=yes
ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=
ac_cv_env_CFLAGS_value=
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CPP_set=
ac_cv_env_CPP_value=
ac_cv_env_GNOMEPRINT_CFLAGS_set=
ac_cv_env_GNOMEPRINT_CFLAGS_value=
ac_cv_env_GNOMEPRINT_LIBS_set=
ac_cv_env_GNOMEPRINT_LIBS_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_LIBS_set=
ac_cv_env_LIBS_value=
ac_cv_env_PKG_CONFIG_set=
ac_cv_env_PKG_CONFIG_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_func_bind_textdomain_codeset=yes
ac_cv_header_inttypes_h=yes
ac_cv_header_libintl_h=yes
ac_cv_header_locale_h=yes
ac_cv_header_memory_h=yes
ac_cv_header_stdc=yes
ac_cv_header_stdint_h=yes
ac_cv_header_stdlib_h=yes
ac_cv_header_string_h=yes
ac_cv_header_strings_h=yes
ac_cv_header_sys_stat_h=yes
ac_cv_header_sys_types_h=yes
ac_cv_header_unistd_h=yes
ac_cv_host=i686-pc-linux-gnu
ac_cv_objext=o
ac_cv_path_EGREP='/bin/grep -E'
ac_cv_path_GREP=/bin/grep
ac_cv_path_INTLTOOL_ICONV=/usr/bin/iconv
ac_cv_path_INTLTOOL_MSGFMT=msgfmt
ac_cv_path_INTLTOOL_MSGMERGE=msgmerge
ac_cv_path_INTLTOOL_PERL=/usr/bin/perl
ac_cv_path_INTLTOOL_XGETTEXT=xgettext
ac_cv_path_MSGFMT=no
ac_cv_path_PKG_CONFIG=/usr/bin/pkg-config
ac_cv_path_install='/usr/bin/install -c'
ac_cv_prog_AWK=mawk
ac_cv_prog_CPP='gcc -E'
ac_cv_prog_ac_ct_CC=gcc
ac_cv_prog_cc_c89=
ac_cv_prog_cc_g=yes
ac_cv_prog_make_make_set=yes
am_cv_CC_dependencies_compiler_type=gcc3
am_cv_val_LC_MESSAGES=yes
gt_cv_func_dgettext_libc=yes
gt_cv_func_dgettext_libintl=no
gt_cv_func_ngettext_libc=yes
gt_cv_have_gettext=no

## ----------------- ##
## Output variables. ##
## ----------------- ##

ACLOCAL='${SHELL} /home/tryscer/Desktop/a4e-0.8.9/missing --run aclocal-1.9'
ALL_LINGUAS='bg ca cs de el es fr he hu it ja lt pl pt ru sk sv ta tr vi zh_CN zh_TW'
AMDEPBACKSLASH='\'
AMDEP_FALSE='#'
AMDEP_TRUE=''
AMTAR='${SHELL} /home/tryscer/Desktop/a4e-0.8.9/missing --run tar'
AUTOCONF='${SHELL} /home/tryscer/Desktop/a4e-0.8.9/missing --run autoconf'
AUTOHEADER='${SHELL} /home/tryscer/Desktop/a4e-0.8.9/missing --run autoheader'
AUTOMAKE='${SHELL} /home/tryscer/Desktop/a4e-0.8.9/missing --run automake-1.9'
AWK='mawk'
CATALOGS=''
CATOBJEXT='NONE'
CC='gcc'
CCDEPMODE='depmode=gcc3'
CFLAGS='-g -O2 -Wall'
CPP='gcc -E'
CPPFLAGS=''
CYGPATH_W='echo'
DATADIRNAME='share'
DEFS='-DHAVE_CONFIG_H'
DEPDIR='.deps'
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP='/bin/grep -E'
EXEEXT=''
GETTEXT_PACKAGE='a4e'
GMOFILES=' bg.gmo ca.gmo cs.gmo de.gmo el.gmo es.gmo fr.gmo he.gmo hu.gmo it.gmo ja.gmo lt.gmo pl.gmo pt.gmo ru.gmo sk.gmo sv.gmo ta.gmo tr.gmo vi.gmo zh_CN.gmo zh_TW.gmo'
GMSGFMT=''
GNOMEPRINT_CFLAGS=''
GNOMEPRINT_LIBS=''
GREP='/bin/grep'
GTK_CFLAGS=''
GTK_LIBS=''
INSTALL_DATA='${INSTALL} -m 644'
INSTALL_PROGRAM='${INSTALL}'
INSTALL_SCRIPT='${INSTALL}'
INSTALL_STRIP_PROGRAM='${SHELL} $(install_sh) -c -s'
INSTOBJEXT=''
INTLLIBS=''
INTLTOOL_CAVES_RULE='%.caves:     %.caves.in     $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_DESKTOP_RULE='%.desktop:   %.desktop.in   $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_DIRECTORY_RULE='%.directory: %.directory.in $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_EXTRACT='$(top_builddir)/intltool-extract'
INTLTOOL_ICONV='/usr/bin/iconv'
INTLTOOL_KBD_RULE='%.kbd:       %.kbd.in       $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u -m -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_KEYS_RULE='%.keys:      %.keys.in      $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -k -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_MERGE='$(top_builddir)/intltool-merge'
INTLTOOL_MSGFMT='msgfmt'
INTLTOOL_MSGMERGE='msgmerge'
INTLTOOL_OAF_RULE='%.oaf:       %.oaf.in       $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -o -p $(top_srcdir)/po $< $@'
INTLTOOL_PERL='/usr/bin/perl'
INTLTOOL_PONG_RULE='%.pong:      %.pong.in      $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_PROP_RULE='%.prop:      %.prop.in      $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_SCHEMAS_RULE='%.schemas:   %.schemas.in   $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -s -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_SERVER_RULE='%.server:    %.server.in    $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -o -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_SERVICE_RULE='%.service: %.service.in   $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_SHEET_RULE='%.sheet:     %.sheet.in     $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_SOUNDLIST_RULE='%.soundlist: %.soundlist.in $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_THEME_RULE='%.theme:     %.theme.in     $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_UI_RULE='%.ui:        %.ui.in        $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_UPDATE='$(top_builddir)/intltool-update'
INTLTOOL_XAM_RULE='%.xam:       %.xml.in       $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
INTLTOOL_XGETTEXT='xgettext'
INTLTOOL_XML_NOMERGE_RULE='%.xml:       %.xml.in       $(INTLTOOL_MERGE) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u /tmp $< $@'
INTLTOOL_XML_RULE='%.xml:       %.xml.in       $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< $@'
LDFLAGS=''
LIBOBJS=''
LIBS=''
LTLIBOBJS=''
MAKEINFO='${SHELL} /home/tryscer/Desktop/a4e-0.8.9/missing --run makeinfo'
MKINSTALLDIRS='./mkinstalldirs'
MSGFMT='no'
MSGFMT_OPTS=''
OBJEXT='o'
PACKAGE='a4e'
PACKAGE_BUGREPORT='tarot@sdf.lonestar.org'
PACKAGE_NAME='a4e'
PACKAGE_STRING='a4e 0.8.9'
PACKAGE_TARNAME='a4e'
PACKAGE_VERSION='0.8.9'
PATH_SEPARATOR=':'
PKG_CONFIG='/usr/bin/pkg-config'
POFILES=' bg.po ca.po cs.po de.po el.po es.po fr.po he.po hu.po it.po ja.po lt.po pl.po pt.po ru.po sk.po sv.po ta.po tr.po vi.po zh_CN.po zh_TW.po'
POSUB='po'
PO_IN_DATADIR_FALSE=''
PO_IN_DATADIR_TRUE=''
SET_MAKE=''
SHELL='/bin/bash'
STRIP=''
USE_NLS='yes'
VERSION='0.8.9'
XGETTEXT=':'
ac_ct_CC='gcc'
am__fastdepCC_FALSE='#'
am__fastdepCC_TRUE=''
am__include='include'
am__leading_dot='.'
am__quote=''
am__tar='${AMTAR} chof - "$$tardir"'
am__untar='${AMTAR} xf -'
bindir='${exec_prefix}/bin'
build='i686-pc-linux-gnu'
build_alias=''
build_cpu='i686'
build_os='linux-gnu'
build_vendor='pc'
datadir='${datarootdir}'
datarootdir='${prefix}/share'
docdir='${datarootdir}/doc/${PACKAGE_TARNAME}'
dvidir='${docdir}'
exec_prefix='${prefix}'
host='i686-pc-linux-gnu'
host_alias=''
host_cpu='i686'
host_os='linux-gnu'
host_vendor='pc'
htmldir='${docdir}'
includedir='${prefix}/include'
infodir='${datarootdir}/info'
install_sh='/home/tryscer/Desktop/a4e-0.8.9/install-sh'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
localedir='/usr/local/share/locale'
localstatedir='${prefix}/var'
mandir='${datarootdir}/man'
mkdir_p='mkdir -p --'
oldincludedir='/usr/include'
pdfdir='${docdir}'
prefix='/usr/local'
program_transform_name='s,x,x,'
psdir='${docdir}'
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
sysconfdir='${prefix}/etc'
target_alias=''

## ----------- ##
## confdefs.h. ##
## ----------- ##

#define PACKAGE_NAME "a4e"
#define PACKAGE_TARNAME "a4e"
#define PACKAGE_VERSION "0.8.9"
#define PACKAGE_STRING "a4e 0.8.9"
#define PACKAGE_BUGREPORT "tarot@sdf.lonestar.org"
#define PACKAGE "a4e"
#define VERSION "0.8.9"
#define STDC_HEADERS 1
#define HAVE_SYS_TYPES_H 1
#define HAVE_SYS_STAT_H 1
#define HAVE_STDLIB_H 1
#define HAVE_STRING_H 1
#define HAVE_MEMORY_H 1
#define HAVE_STRINGS_H 1
#define HAVE_INTTYPES_H 1
#define HAVE_STDINT_H 1
#define HAVE_UNISTD_H 1
#define HAVE_LOCALE_H 1
#define HAVE_LC_MESSAGES 1
#define HAVE_BIND_TEXTDOMAIN_CODESET 1
#define HAVE_GETTEXT 1
#define LOCALEDIR "/usr/local/share/locale"

configure: exit 0

---

### Post by bagofchickens on 2007-12-03
Tryscer, I'm not sure if I could be of help here, but to anyone interested, just as a prove of concept, I managed to achieve something similar with [_Kommander_]("http://kommander.kdewebdev.org/") by modifying [_this handy script_]("http://www.kde-apps.org/content/show.php/Notepad?content=54687"). Keep in mind that there's a serious possibility of some unexpected glitches. *Any* kind of modifications and improvements will be highly appreciated! I am running it under Kubuntu, so you'll need at least **kmdr-executor** and  **kstart**.

Unarchive textroom.kmdr.tar.gz and start textroom.kmdr with

```
kstart --windowclass "kmdr-executor" --fullscreen kmdr-executor /PATH/TO/textroom.kmdr
```

You can also open files on startup by using a bash script file:

```
#!/bin/sh
kstart --windowclass "kmdr-executor" --fullscreen kmdr-executor /PATH/TO/textroom.kmdr ifile=$1
```

Font name, size and colors are configurable through kmdr-editor, in case you are willing to make minor changes.

---

### Post by Falc on 2008-01-06
I tried out the emacs method on page 1 of this thread but I wasn't too happy with it.

First off, emacs 22 has a --fullscreen command line option, so no more need for wmctrl. I don't think you can leave emacs' own fullscreen though, but I'm not even sure you could with wmctrl.

Second, the method used to make the column is a bit of a hack. It tries its best to fake it by indenting lines, but if you delete a bit too much you eat away your margin.

No, a much better method is emacs' fringes. Those are the two colored bands on the left and right of your editing area and you set their width (in pixels!) with set-fringe-mode. Plus, you can control their color through the standard faces system. You get a column mode that won't break like the indent one does.

---

### Post by jenik on 2008-01-07
a4e is great, almost perfect!!! thanks a lot. is there anything going on about it? any new versions?

---

### Post by rougier on 2008-01-08
Hi all,

I've heavily modified the pyroom.py posted by Nowhereman to allows several buffers, undo/redo and line numbers. There are three different styles defined and it is quite easy to add new styles.

Usage:
----------

pyroom.py [-style] file1 file2 ...
style can be either 'blue', 'green' or 'darkgreen'


Commands:
-----------------

Control-H: Show help in a new buffer
Control-I: Show buffer information
Control-L: Toggle line number
Control-N: Create a new buffer
Control-O: Open a file in a new buffer
Control-Q: Quit
Control-S: Save current buffer
Control-Shift-S: Save current buffer as
Control-W: Close buffer and exit if it was the last buffer
Control-Y: Redo last typing
Control-Z: Undo last typing
Control-Left: Switch to previous buffer
Control-Right: Switch to next buffer

Warnings:
--------------
No autosave.
No question whether to close a modified buffer or not


Nicolas


```


#! /usr/bin/env python
# ------------------------------------------------------------------------------
# PyRoom - A clone of WriteRoom
# Copyright (c) 2007 Nicolas P. Rougier & NoWhereMan
#
# This program is free software: you can redistribute it and/or modify it under
# the terms of the GNU General Public License as published by the Free Software
# Foundation, either version 3 of the License, or (at your option) any later
# version.
#
# This program is distributed in the hope that it will be useful, but WITHOUT
# ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS
# FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License along with
# this program.  If not, see <http://www.gnu.org/licenses/>.
# ------------------------------------------------------------------------------
#
# Based on code posted on ubuntu forums by NoWhereMan (www.nowhereland.it)
#  (Ubuntu thread was "WriteRoom/Darkroom/?")
#  
# ------------------------------------------------------------------------------

import traceback
import sys, os.path
import gobject, gtk, pango, gtksourceview

# Some styles
styles = {
    'darkgreen' : {
        'name'       : 'darkgreen',
        'background' : '#000000',
        'foreground' : '#007700',
        'lines'      : '#001100',
        'border'     : '#001100',
        'info'       : '#007700',
        'font'       : 'DejaVu Sans Mono 14',
        'padding'    : 6,
        'size'       : [0.6, 0.95] # [width, height]
        },
    'green': {
        'name'       : 'green',
        'background' : '#000000',
        'foreground' : '#00ff00',
        'lines'      : '#007700',
        'border'     : '#003300',
        'info'       : '#00ff00',
        'font'       : 'DejaVu Sans Mono 14',
        'padding'    : 6,
        'size'       : [0.6, 0.95] # [width, height]
        },
    'blue': {
        'name'       : 'blue',
        'background' : '#0000ff',
        'foreground' : '#ffffff',
        'lines'      : '#5555ff',
        'border'     : '#3333ff',
        'info'       : '#ffffff',
        'font'       : 'DejaVu Sans Mono 14',
        'padding'    : 6,
        'size'       : [0.6, 0.95] # [width, height]
        }
    }

FILE_UNNAMED = "* Unnamed *"

HELP = """PyRoom - an adaptation of write room
Copyright (c) 2007 Nicolas Rougier, NoWhereMan

This program is free software: you can redistribute it and/or modify it under
the terms of the GNU General Public License as published by the Free Software
Foundation, either version 3 of the License, or (at your option) any later
version.

Usage:
------

pyroom.py [-style] file1 file2 ...
style can be either 'blue', 'green', 'darkgreen'


Commands:
---------
Control-H: Show help in a new buffer
Control-I: Show buffer information
Control-L: Toggle line number
Control-N: Create a new buffer
Control-O: Open a file in a new buffer
Control-Q: Quit
Control-S: Save current buffer
Control-Shift-S: Save current buffer as
Control-W: Close buffer and exit if it was the last buffer
Control-Y: Redo last typing
Control-Z: Undo last typing
Control-Left: Switch to previous buffer
Control-Right: Switch to next buffer

Warnings:
---------
No autosave.
No question whether to close a modified buffer or not
"""


class FadeLabel (gtk.Label):
    """ GTK Label with timed fade out effect """

    active_duration = 3000      # Fade start after this time
    fade_duration   = 1500      # Fade duration

    def __init__ (self, str='', active_color=None, inactive_color=None):
        gtk.Label.__init__ (self, str)
        if not active_color:
            active_color = "#ffffff"
        self.active_color = active_color
        if not inactive_color:
            inactive_color = "#000000"
        self.inactive_color = inactive_color
        self.idle = 0

    def set_text (self, str, duration=None):
        if not duration:
            duration = self.active_duration
        self.modify_fg (gtk.STATE_NORMAL,gtk.gdk.color_parse(self.active_color))
        gtk.Label.set_text (self, str)
        if self.idle:
            gobject.source_remove (self.idle)
        self.idle = gobject.timeout_add (duration, self.fade_start)

    def fade_start (self):
        self.fade_level = 1.0
        if self.idle:
            gobject.source_remove (self.idle)
        self.idle = gobject.timeout_add (25, self.fade_out)
        
    def fade_out (self):
        color = gtk.gdk.color_parse (self.inactive_color)
        r1, g1, b1 = color.red, color.green, color.blue
        color = gtk.gdk.color_parse (self.active_color)
        r2, g2, b2 = color.red, color.green, color.blue
        r = r1 + int(self.fade_level*abs (r1-r2))
        g = g1 + int(self.fade_level*abs (g1-g2))
        b = b1 + int(self.fade_level*abs (b1-b2))
        self.modify_fg (gtk.STATE_NORMAL, gtk.gdk.Color (r,g,b))
        self.fade_level -= 1.0 / (self.fade_duration / 25)
        if (self.fade_level > 0):
            return True
        self.idle = 0
        return False

	
class PyRoom:
    """ The PyRoom class"""

    buffers = []
    current = 0

    def __init__(self, style):

        self.style = style

        # Main window
        self.window = gtk.Window (gtk.WINDOW_TOPLEVEL)
        self.window.set_name ("PyRoom")
        self.window.fullscreen ()
        self.window.connect ("delete_event", self.delete_event)
        self.window.connect ("destroy", self.destroy)

        self.textbox = gtksourceview.SourceView()
        self.new_buffer()
        self.textbox.connect ('scroll-event', self.scroll_event)
        self.textbox.connect ('key-press-event', self.key_press_event)
        self.textbox.set_wrap_mode (gtk.WRAP_WORD)

        self.fixed = gtk.Fixed()
        self.vbox = gtk.VBox()
        self.window.add (self.fixed)
        self.fixed.put (self.vbox, 0,0)

        self.boxout = gtk.EventBox()
        self.boxout.set_border_width (1)
        self.boxin = gtk.EventBox()
        self.boxin.set_border_width (1)
        self.vbox.pack_start (self.boxout, True, True, 6)
        self.boxout.add (self.boxin)

        self.scrolled = gtk.ScrolledWindow()
        self.boxin.add (self.scrolled)
        self.scrolled.add (self.textbox)
        self.scrolled.set_policy(gtk.POLICY_NEVER, gtk.POLICY_NEVER)
        self.scrolled.show()
        self.scrolled.set_property ("resize-mode", gtk.RESIZE_PARENT)
        self.textbox.set_property ("resize-mode", gtk.RESIZE_PARENT)
        self.vbox.set_property ("resize-mode", gtk.RESIZE_PARENT)
        self.vbox.show_all()

        # Status
        self.status = FadeLabel ()
        self.hbox = gtk.HBox ()
        self.hbox.set_spacing (12)        
        self.hbox.pack_end (self.status, True, True, 0)
        self.vbox.pack_end (self.hbox, False, False, 0)
        self.status.set_alignment (0.0, 0.5)
        self.status.set_justify (gtk.JUSTIFY_LEFT)
        self.apply_style ()
        self.window.show_all ()        
        self.status.set_text ('Welcome to PyRoom 1.0, type Control-H for help')

    def delete_event(self, widget, event, data=None):
        """ Quit """
        return False

    def destroy(self, widget, data=None):
        """ Quit """
        gtk.main_quit()

    def key_press_event (self, widget, event):
        """ key press event dispatcher """

        bindings = {
            gtk.keysyms.Left : self.prev_buffer,
            gtk.keysyms.Right: self.next_buffer,
            gtk.keysyms.h:     self.show_help,
            gtk.keysyms.i:     self.show_info,
            gtk.keysyms.l:     self.toggle_lines,
            gtk.keysyms.n:     self.new_buffer,
            gtk.keysyms.o:     self.open_file,
            gtk.keysyms.q:     self.quit,
            gtk.keysyms.s:     self.save_file,
            gtk.keysyms.w:     self.close_buffer,
            gtk.keysyms.y:     self.redo,
            gtk.keysyms.z:     self.undo
            }
        if event.state & gtk.gdk.CONTROL_MASK:
            # Special case for Control-Shift-s
            if (event.state & gtk.gdk.SHIFT_MASK):
                print event.keyval
            if (event.state & gtk.gdk.SHIFT_MASK) and (event.keyval == gtk.keysyms.S):
                self.save_file_as()                
                return True
            if bindings.has_key (event.keyval):
                bindings [event.keyval]()
                return True
        return False

    def scroll_event (self, widget, event):
        """" Scroll event dispatcher """

        if event.direction == gtk.gdk.SCROLL_UP:
            self.scroll_up()
        elif event.direction == gtk.gdk.SCROLL_DOWN:
            self.scroll_down()

    def show_help (self):
        """ Create a new buffer and inserts help """
        
        buffer = self.new_buffer()
        buffer.begin_not_undoable_action()
        buffer.set_text (HELP)
        buffer.end_not_undoable_action()

    def new_buffer (self):
        """ Create a new buffer """

        buffer = gtksourceview.SourceBuffer()
        buffer.set_check_brackets (False)
        buffer.set_highlight (False)
        buffer.filename = FILE_UNNAMED
        self.buffers.insert (self.current+1, buffer)
        buffer.place_cursor(buffer.get_start_iter())
        self.next_buffer ()
        return buffer

    def close_buffer (self):
        """ Close current buffer """

        if len(self.buffers) > 1:
            self.buffers.pop (self.current)
            self.current = min (len(self.buffers)-1, self.current)
            self.set_buffer (self.current)
        else:
            quit()

    def set_buffer (self, index):
        """ Set current buffer """

        if index >= 0 and index < len(self.buffers):
            self.current = index
            buffer = self.buffers[index]
            self.textbox.set_buffer (buffer)
            if hasattr (self, 'status'):
                self.status.set_text ('Switching to buffer %d (%s)' % (
                        (self.current+1), buffer.filename))

    def next_buffer (self):
        """ Switch to next buffer """        

        if self.current < (len(self.buffers)-1):
            self.current += 1
        else:
            self.current = 0
        self.set_buffer (self.current)

    def prev_buffer (self):
        """ Switch to prev buffer """

        if self.current > 0:
            self.current -= 1
        else:
            self.current = len(self.buffers)-1
        self.set_buffer (self.current)

    def apply_style (self, style=None):
        """ """

        if style:
            self.style = style
        self.window.modify_bg (gtk.STATE_NORMAL,
                               gtk.gdk.color_parse(self.style['background']))
        self.textbox.modify_bg (gtk.STATE_NORMAL,
                                gtk.gdk.color_parse(self.style['background']))
        self.textbox.modify_base (gtk.STATE_NORMAL,
                                  gtk.gdk.color_parse(self.style['background']))
        self.textbox.modify_text (gtk.STATE_NORMAL,
                                  gtk.gdk.color_parse(self.style['foreground']))
        self.textbox.modify_fg (gtk.STATE_NORMAL,
                                gtk.gdk.color_parse(self.style['lines']))
        self.status.active_color = self.style['foreground']
        self.status.inactive_color = self.style['background']
        self.boxout.modify_bg (gtk.STATE_NORMAL,
                               gtk.gdk.color_parse (self.style['border']))
        self.textbox.modify_font (pango.FontDescription (self.style['font']))

        gtk.rc_parse_string (
            """
	    style "pyroom-colored-cursor" {
                GtkTextView::cursor-color = '""" + self.style['foreground'] + """'
            }
            class "GtkWidget" style "pyroom-colored-cursor"
	    """)
        w,h = gtk.gdk.screen_width(), gtk.gdk.screen_height()
        width  = int (self.style['size'][0]*w)
        height = int (self.style['size'][1]*h)
        self.vbox.set_size_request (width, height)
        self.fixed.move (self.vbox,
                         int((1-self.style['size'][0])*w/2),
                         int((1-self.style['size'][1])*h/2))
        self.textbox.set_border_width (self.style['padding'])
                    
    def word_count(self, buffer):
        """ Word count in a text buffer """

        i1 = buffer.get_start_iter()
        i2 = i1.copy()
        i2.forward_word_end()
        i = 0
        while i2.get_offset() <> i1.get_offset():
            i += 1
            i1 = i2.copy()
            i2.forward_word_end()
        return i

    def quit(self):
        """ quit pyroom """
        gtk.main_quit()

    def show_info (self):
        """ Display buffer information on status label for 5 seconds """

        buffer = self.buffers[self.current]
        if buffer.can_undo() or buffer.can_redo():
            status = ' (modified)'
        else:
            status= ''
        self.status.set_text (
            "Buffer %d: %s%s, %d byte(s), %d word(s), %d line(s)" % (
                self.current+1,
                buffer.filename,
                status,
                buffer.get_char_count(),
                self.word_count (buffer),
                buffer.get_line_count(),
                ), 5000
            )

    def scroll_down (self):
        """ Scroll window down """
        adj = self.scrolled.get_vadjustment()
        if adj.upper > adj.page_size:
            adj.value = min (adj.upper-adj.page_size,
                             adj.value+adj.step_increment)

    def scroll_up (self):
        """ Scroll window up """
        adj = self.scrolled.get_vadjustment()
        if adj.value  > adj.step_increment:
            adj.value -= adj.step_increment
        else:
            adj.value = 0

    def undo (self):
        """ Undo last typing """
        buffer = self.textbox.get_buffer()
        if buffer.can_undo():
            buffer.undo()
        else:
            self.status.set_text ('No more undo !')

    def redo (self):
        """ Redo last typing """
        buffer = self.textbox.get_buffer()
        if buffer.can_redo():
            buffer.redo()
        else:
            self.status.set_text ('No more redo !')

    def toggle_lines (self):
        """ Toggle lines number """
        b = self.textbox.get_show_line_numbers()
        b = not b
        self.textbox.set_show_line_numbers (b)

    def open_file(self):
        """ Open file """
        chooser = gtk.FileChooserDialog(
            'PyRoom', self.window, gtk.FILE_CHOOSER_ACTION_OPEN,
            buttons=(gtk.STOCK_CANCEL, gtk.RESPONSE_CANCEL,
                     gtk.STOCK_OPEN, gtk.RESPONSE_OK))
        chooser.set_default_response(gtk.RESPONSE_OK)

        res = chooser.run()
        if res == gtk.RESPONSE_OK:
            buffer = self.new_buffer ()
            buffer.filename = chooser.get_filename()
            try:
                f = open (buffer.filename, 'r')
                buffer = self.buffers[self.current]
                buffer.begin_not_undoable_action()
                utf8 = unicode (f.read(), 'utf-8')
                buffer.set_text(utf8)
                buffer.end_not_undoable_action()
                f.close()
                self.status.set_text('File ' + buffer.filename + ' open')
            except:
                buffer.set_text ('Unable to open %s\n %s\n' %
                                 (buffer.filename, traceback.format_exc()))
                self.status.set_text('Failed to open ' + buffer.filename)
                buffer.filename = FILE_UNNAMED
        else:
            self.status.set_text( 'Closed, no files selected' )
        chooser.destroy()
        
    def save_file(self):
        """ Save file """

        buffer = self.buffers[self.current]
        if buffer.filename != FILE_UNNAMED:
            f = open (buffer.filename, 'w')
            txt = buffer.get_text (buffer.get_start_iter(),
                                   buffer.get_end_iter())
            f.write(txt)
            f.close()
            buffer.begin_not_undoable_action()
            buffer.end_not_undoable_action()
            self.status.set_text('File ' + buffer.filename + ' saved')
        else:
            self.save_file_as ()
            
    def save_file_as (self):
        """ Save file as """

        buffer = self.buffers[self.current]
        chooser = gtk.FileChooserDialog(
            'PyRoom', self.window, gtk.FILE_CHOOSER_ACTION_SAVE,
            buttons=(gtk.STOCK_CANCEL, gtk.RESPONSE_CANCEL,
                     gtk.STOCK_SAVE,   gtk.RESPONSE_OK))
        chooser.set_default_response (gtk.RESPONSE_OK)
        if buffer.filename != FILE_UNNAMED:
            chooser.set_filename (buffer.filename)
        res = chooser.run()
        if res == gtk.RESPONSE_OK:
            buffer.filename = chooser.get_filename()
            self.save_file ()
        else:
            self.status.set_text( 'Closed, no files selected' )
        chooser.destroy()


if __name__ == "__main__":
    style = 'blue'
    files = []

    # Look for style and file on command line
    for arg in sys.argv[1:]:
        if arg[0] == '-':
            t = arg[1:]
            if styles.has_key(arg[1:]):
                style = arg[1:]
        else:
            files.append (arg)

    # Create relevant buffers for file and load them
    pyroom = PyRoom (styles[style])
    if len(files):
        for file in files:
            buffer = pyroom.new_buffer()
            buffer.filename = file
            if os.path.exists (file):
                try:
                    print file
                    f = open (file, 'r')
                    buffer.begin_not_undoable_action()
                    utf8 = unicode (f.read(), 'utf-8')
                    buffer.set_text (utf8)
                    buffer.end_not_undoable_action()
                    f.close()
                except:
                    buffer.set_text ('Unable to open ' + buffer.filename + '\n')
                    buffer.set_text ('Unable to open %s\n %s\n' %
                                     (buffer.filename, traceback.format_exc()))
                    buffer.filename = FILE_UNNAMED
        pyroom.set_buffer (0)
        pyroom.close_buffer()            
    gtk.main()

```

---

### Post by bagofchickens on 2008-01-08
Here's another take on TextRoom. This time it does not depend on Kommander. To compile it, you'll need  the Qt4 development libraries. Then, as usual:

```

tar xjvf ./textroom-0.2.2.tar.bz2
cd ./textroom-0.2.2
qmake-qt4
make
sudo make install
```

Start the editor by typing:

```
textroom
```

and press F1 for help.

Visit the [TextRoom Wiki]("http://code.google.com/p/textroom/w/list") for more details.

Parts of the code are from another similar project by Jacob Rideout at [http://code.google.com/p/phrasis/]("http://code.google.com/p/phrasis/"). Unfortunately, it seems that Phrasis has not been updated for nearly a year now, but it looks very promising.

Help and suggestions (especially help because I really need a good program like that, no matter who wrote it) are welcomed.  If anyone has hacked around the editor, please post your patches or instructions here. You are also welcome to commit [directly]("http://code.google.com/p/textroom/").

**Changelog**:

ver.0.2.2 - 2008-02-09

* the project is now hosted by [code.google.com]("http://code.google.com/p/textroom/")
* added "Flow mode" option (thanks to [zebulon M]("http://ubuntuforums.org/member.php?u=408505"))
* rearranged Options dialog
* textroom.pro is now set to "release" mode

ver.0.2.1 - 2008-01-31

* added "Auto save" option (thanks to [adamvert]("http://ubuntuforums.org/member.php?u=1513"))
* minor bugfixes

**[Download TextRoom]("http://code.google.com/p/textroom/downloads/list")**

---

### Post by adamvert on 2008-01-30
Textroom is great, works pretty well.  Are you planning to work on it any more?  Autosaving would be great...  Also it would be nice to use standard keys - F11 to go fullscreen, ESC to leave fullscreen.  And *minimal* formatting (bold and italic)(although some might say this defeats the object).

BTW, it flips out a bit when I use alt-tab (with compiz - in metacity it works fine).

Thanks!
Adam

---

### Post by bagofchickens on 2008-01-30
Hey, thanks for the input. Yes, I do plan to work on Textroom, though I'm still a rookie in Qt, so my initial warning on NOT using it with important files stays intact. You can now use F11 and the Escape key as you requested. I'll also add autosave option as soon as possible. I was thinking exactly the same thing about bold and italic because I need it too. Maybe in future versions I'll add support for rich text formatting.

And, yes, there's something wrong with how Compiz handles active windows in Textroom. I am running Kwin, so it took me a while to notice this. Could someone else also confirm the problem?

[SIZE="1"][Download TextRoom v.0.2 here.]("http://ubuntuforums.org/showpost.php?p=4098915&postcount=51")[/SIZE]

---

### Post by adamvert on 2008-01-31
OK, so I went ahead and added the auto-save functionality myself - hope you don't mind... :)

There's an "Auto Save" checkbox in the options box, and if it's checked, the file gets autosaved every 5 keystrokes.  I also added the F11 shortcut for fullscreen.  

Again, I would advise not using this for important files (although I haven't had any problems yet).

---

### Post by adamvert on 2008-01-31
D'oh!  Sorry, only just saw yr reply.  I guess we should merge somehow (unless you want to implement the autosave yrself)

I'm also pretty clueless about Qt (never used it before), so let's hope no-one takes us too seriously :)

---

### Post by bagofchickens on 2008-01-31
> **adamvert said:**
> I guess we should merge somehow

We definitely should! :guitar:

Edit: OK, I just merged your changes along with some minor bug fixes I had already noticed in 0.2b. Now it's ver. 0.2.1

[SIZE="1"][Download TextRoom v.0.2.1 here]("http://ubuntuforums.org/showpost.php?p=4098915&postcount=51").[/SIZE]

---

### Post by BrunoBord on 2008-02-03
Continuing the quite well done work by NoWhereMan and Nicolas P. Rougier, I've opened a Pyroom project on Launchpad.

[https://launchpad.net/pyroom](https://launchpad.net/pyroom)

Anyone willing to contribute is welcome!

---

### Post by NoWhereMan on 2008-02-03
what the hell?? :D I didn't even see rougier's post :D kudos for that!

and kudos to you too!

only one thing: IMO the editor border shouldn't be visible

now, for your pleasure (lol):

Other features of course might be the ability to change colors and store settings in .config/ or .pyroomrc or something...

of course autosave, and maybe re-open the last file you were editing last time you closed the editor.

nice touch the fading label. multiple buffers are l33t, but I use a lot ctrl+arrows to move word by word, maybe changing it to ctrl+pgUp/Down (actually for me ANY cursor combo is potentially harmful :/) ?

Now if only I can stop myself using :q! to quit... :D

bye!

---

### Post by BrunoBord on 2008-02-04
> **NoWhereMan said:**
> only one thing: IMO the editor border shouldn't be visible

You mean Window border? or the margin mark on both left and right side?...

> Other features of course might be the ability to change colors and store settings in .config/ or .pyroomrc or something...

Planned, thanks.

> of course autosave

Planned too ;)

> and maybe re-open the last file you were editing last time you closed the editor.

Interesting, I'll add it to my TODO list.

> nice touch the fading label. multiple buffers are l33t, but I use a lot ctrl+arrows to move word by word, maybe changing it to ctrl+pgUp/Down (actually for me ANY cursor combo is potentially harmful :/) ?

Will have to rethink about it. Any Usability expert here? ;)

Thank you for the feedback!

---

### Post by NoWhereMan on 2008-02-04
> **BrunoBord said:**
> You mean Window border? or the margin mark on both left and right side?...

there is a small editor border, it is set by the boxout bg, took from the 'border' property of the hashed list of styles

> Will have to rethink about it. Any Usability expert here? ;)

**here I am! **

j/k :D I've only followed (and passed) a course for my CS degree...

I don't know if we could call it not-usable, it's probably an inconsistency with how the editors usually works c+pgup/down works, but it seem like it is used to go to line start/end...

I'm not sure really if it's worth having multiple buffers at all... it's supposed to be a distraction-free editor, you know, so you probably concentrate better on one document at a time (but this might be  a matter of taste) ;)

from a usability point of view the document should probably be auto-saved on exit, otherwise it quits with no question and I might have lost all of my changes

last thing: the caret should be put at the start of the buffer when you load a new file :)

keep up the good work

---

### Post by BrunoBord on 2008-02-04
> keep up the good work

Manu thanks indeed, I'll try to do my best.
BTW, any bug / feature request / suggestion may be submitted via a bug report on Launchpad.

[https://bugs.launchpad.net/pyroom/](https://bugs.launchpad.net/pyroom/)

---

### Post by maruchan on 2008-02-05
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/pyroom/+bug/189261](https://bugs.launchpad.net/pyroom/+bug/189261) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I created an amber theme for PyRoom:

```

    'amber' : {
        'name'       : 'amber',
        'background' : '#151000',
        'foreground' : '#AE8400',
        'lines'      : '#AE8400',
        'border'     : '#151000',
        'info'       : '#AE8400',
        'font'       : 'DejaVu Sans Mono 9',
        'padding'    : 8,
        'size'       : [0.45, 0.75] # [width, height]
        },

```

I also tried to come close to the width/height proportions I saw on screenshots at the writeroom site, since I'm sure they use a preselected proportion of screen space, perhaps based on the golden mean (it's been a while and I was a little impatient so I didn't do the research here).

I'm also not sure what "lines" color does...

Here's a screenshot: [http://www.friendlyskies.net/pyroom.png](http://www.friendlyskies.net/pyroom.png)

Thanks for this excellent project!

---

### Post by zebulon M on 2008-02-06
I like the Textroom and I made a little addition to it.

You can now disable backspace and delete by checking a "flow mode" box in the options.

That may seem crazy but for some of us this little feature is very useful. It is intended to help letting the writing progress and not letting minor typos and errors stop the writers "flow". A bad typist kind of backspace his way through the text, this feature will help by forcing the writer to be more careful, and hopefully he'll learn to type better. It may also be good for perfectionists, which can get stuck in a paragraph for half an hour, trying to get it right. The flow mode will force them to progress. Without instant editing, u must also plan your writing a little better, more like in the ancient times with type writers.

There will of course still be typos and errors, these are taken care of at a second pass of the text, maybe in your usual word processor.

If u like to try it, u can download here and install exactly like Bagofchickens describes, a few posts ago. If u like my little hack, let it be known, maybe Bagofchickens will include it into the main branch. ;)

/Magnus

---

### Post by bagofchickens on 2008-02-09
Wow, somehow I managed to miss all the latest around PyRoom's development. Since it's picking up steam, this is just a quick note on TextRoom (no hijacking intended). The "Flow mode" option is now merged with ver 0.2.2. You can follow all the current and subsequent changes on [my initial post]("http://ubuntuforums.org/showpost.php?p=4098915&postcount=51") until I finally wrap my head around some more convenient code management system.

By the way, zebulon M, the Delete and Backspace keys idea is so twisted, it's actually cool :) I never would've thought of this, thanks for bringing it in.

Edit: Well, the project is now available [here]("http://code.google.com/p/textroom/") officially.

---

### Post by ffahog on 2008-02-13
I'm trying to download and install / run the newest version of JDarkRoom, which is a program that I loved to use back when I was running XP.

The download file from the official website is a JAR file. When I double-click on it, Ubuntu opens it up using the archive manager. When I right click on the file and choose "Open with 'Sun Java 6 Runtime'" nothing happens. When I open a terminal and write:

```
java -jar JDarkRoom.jar
```

It tells me: "Unable to access jarfile JDarkRoom.jar"

I get similar results after I extract JDarkRoom into a directory and try to open / run it.


Can anyone help me get the program up and running?

---

### Post by xer0kill on 2008-02-26
That's a strange problem. I could never get JDarkroom to run properly for me (maybe cause i'm using 64bit Ubuntu?)

What I'm using right now is RubyRoom.[http://rubyroom.rubyforge.org/](http://rubyroom.rubyforge.org/)
To use it, you'll need to install ruby and ruby-gnome2 via synaptic. Then, run "ruby rubyroom.rb"

---

### Post by timmie on 2008-02-26
Hey, this works out of the box:
[http://effbot.org/zone/vroom.htm](http://effbot.org/zone/vroom.htm)
```

svn co http://svn.effbot.python-hosting.com/stuff/zone/vroom vroom
cd vroom
python vroom.py
```

---

### Post by Abras on 2008-04-01
I apologize for bumping this thread, but I happened to notice on the pyroom launchpad page that it is still being actively developed (the last update was March 30), so I am curious as to when version 0.2 will be officially released. I just wanted to let you know that at least one person is anticipating the release. But you better get it out soon. You don't want angry mob to form do you? (hypothetical question: Can a mob consist of one person?)

---

### Post by HeresJohnny on 2008-04-13
Thanks, ryorininseven and NoWhereMan!  Thanks to you I have JDarkRoom up and running on my 64-bit Hardy beta laptop.  It works absolutely perfectly!  I might follow your suggestions later on because I have a text box, but the fullscreen black treatment rids me of all distractions.  As an extra added bonus, I can even type in Korean using SCIM if I want to (not that it'll happen often).  I am really, REALLY happy that you got this done for the millions -- AND MILLIONS-- of fans, cheering your names...  I was looking for the thank you button, but couldn't find it.  Oh well, consider yourselves thanked for putting this together.  Youse guys are awesome!:guitar:

---

### Post by mormor on 2008-06-23
Im not totally shure what happened during this post. 3 diferent developers merged into the development of PyRoom?

I have a PyRoom question actually. :P So I hope this is the right place.

The reason I found out about PyRoom is the simular app named Q10. Q10 also has typingsounds(old typewriter type, actually from the movie Amelie). But still I would like to ask if this would be a posibility to add easily as a optional feature.? I use PyRoom, and its perfect for blocking out the rest of the world.

Also if you could att a "chickchickchikcchaching"-sound on lineshifting. J/K. THat would maybe be a bit ower the top.

Anywa. PyRoom is great, Im not shure if I should try any of the other aps in the thread. If I should, please point me in the right direction.

---


---
title: "Help: My GTK engines won't recognize their themes"
date: 2010-09-07
forum: Desktop Environments
---

### Post by carlossl on 2010-09-07
Hi!

I just installed Ubuntu Karmic 9.10 64 bits in my laptop because its kernel version is the only one that will recognize my fan, so upgrading to another version of Ubuntu is not a solution to this problem:

So far everything has been working correctly except the capability of some GTK engines to recognize themes: **they look like Windows 95** (I'm guessing they take the Raleigh GTK theme because they don't recognize the one I installed).

I've installed, uninstalled and reinstalled several times the Murrine, Equinox, Aurora and Pixbuf GTK engines, without luck. I've installed them from Synaptics (adding the source for some of them) or downloading them from gnome-look, but the problem persists.
The themes I've been trying to install are these two:

[LIST]
[*] [ffuu theme from gnome-look.org]("http://gnome-look.org/content/show.php?content=127731&forumpage=0")
[*] [Arbeit AE Darker theme from gnome-look.org]("http://gnome-look.org/content/show.php/Arbeit+AE+Darker?content=128438")
[/LIST]

They both use Equinox, Aurora and Murrine. I'm guessing the problem is with the Murrine engine, because the "New Wave" theme that comes installed by default with Ubuntu doesn't look right either, and it uses that engine.

I don't know what else to do, I disabled the Compiz effects but the problem is still there.


**_Edit_**:

I found 4 threads with a similar problem, but there's still no official solution, just patches or temporary solutions:

[LIST]
[*] [Windows are loading the wrong theme]("http://ubuntuforums.org/showthread.php?t=844888")
[*] [Can't change Gnome themes]("http://ubuntuforums.org/showthread.php?t=998253")
[*] [A Problem regarding themes]("http://ubuntuforums.org/showthread.php?t=1560754")
[*] [A Problem regarding themes]("http://ubuntuforums.org/showthread.php?t=1560754")
[*] [Themes don't work in edgy gnome?]("http://ubuntuforums.org/showthread.php?t=288105")
[/LIST]

Anybody knows what the solution could be?

Thanks in advance!

---

### Post by carlossl on 2010-09-07
Ok, I found out where the problem comes from, but still don't have a solution.

I downloaded the *ffuu* theme I mentioned in the first post, extracted it to my .themes directory and applied it going to System->Preferences->Appearance->Customize and selecting the ffuu gtk style in the Controls tab. The style now looks like an ugly Windows 95 theme.

Then I opened a terminal and typed:

```
sudo /usr/sbin/synaptic
```

and here's the error that appeared:

```
/root/.themes/ffuu/gtk-2.0/panel.rc:78: error: unexpected identifier `textstyle', expected character `}'
/root/.themes/ffuu/gtk-2.0/gtkrc:121: error: unexpected identifier `arrowstyle', expected character `}'
```

The problem also appears if I open an application without root privileges (I made a symlink from my .themes directory to the root directory). For example:

```
/usr/sbin/synaptic
```

Throws the exact same error, but pointing to /home/myuser/.themes ...

So this seems to be a problem with Murrine, because line 78, as the first error says, belongs to the Murrine section:

```
style "theme-panel-light"
{
    xthickness        = 1
    ythickness        = 0

    fg[NORMAL]    = @fg_color

    engine "murrine" {
        textstyle = 1      ## LINE 78
        roundness = 0
    }
}

```

And line 121 in gtkrc, as the second error says, also belongs to the Murrine section:

```

engine "murrine"

	{

		animation           = TRUE
		arrowstyle          = 1       ## LINE 121		
		border_shades       = { 1.2, 1.0 }
		.
		.
		.

```

I'll keep looking, since it seems that Murrine is the problem, because it doesn't recognize any theme.

---


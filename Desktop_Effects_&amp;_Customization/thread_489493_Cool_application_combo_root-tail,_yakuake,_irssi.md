---
title: "Cool application combo: root-tail, yakuake, irssi"
date: 2007-07-01
forum: Desktop Effects &amp; Customization
---

### Post by Ceriel Nosforit on 2007-07-01
There are more things you can do to pimp your desktop than install Beryl/Compiz. This is one of them. It requires a whole lot of fiddling, and **for the sake of this guide KDE**, but the end result is both cool and useful.

Here are two screenshots of what you can have the end-result look like:

[[IMG]http://img338.imageshack.us/img338/6830/snapshot4ev3.th.png[/IMG]](http://img338.imageshack.us/my.php?image=snapshot4ev3.png)

This is the output of [FONT="Courier New"]root-tail[/FONT] reading the log file that [FONT="Courier New"]irssi[/FONT] creates as it is running. You can always read the latest line someone wrote in an IRC channel you're connected to. In order to reply you press F12 which brings up this view:

[[IMG]http://img507.imageshack.us/img507/435/snapshot3rj9.th.png[/IMG]](http://img507.imageshack.us/my.php?image=snapshot3rj9.png)

This is the [FONT="Courier New"]yakuake[/FONT] console, inspired by the console found in Quake and many other First-Person-Shooter games. While it is useful for many other things, the program I have running in it is the [FONT="Courier New"]irssi[/FONT] Internet Relay Chat (IRC) client. Configuring [FONT="Courier New"]irssi[/FONT] is a lesser science on its own, but lets not worry about that just yet. 

In order to get a set-up like mine, the first program you'll want to install is probably yakuake, the program which behaves like the console in quake. 

To install it, simply issue this command in your console:
```
sudo apt-get install yakuake
```

Now run the program. It should be located in your menu, but if not you can call it directly from the shell by issuing "yakuake". Press F12, and behold the slick console. The small arrow among the three buttons to the lower right of yakuake opens a menu which lets you configure it, but to get the nice transparency effect you need to change the schema used by "konsole", the default terminal in KDE. Start up konsole, got to Settings -> Configure Konsole -> Schema, and begin fiddling until it looks like you want it. Konsole will ask to save the schema automatically when you press OK, but you need to make sure yakuake is using the same schema. Do that by right-clicking in the yakuake window and look up the appropriate setting. 


Next up is irssi. Press F12 to bring down yakuake and issue the following command to install it:

```
sudo apt-get install irssi
```

To really get the hang of the program you need to read the [documentation]("http://irssi.org/documentation"), but if you're impatient, here's a way to be a bit quicker about it. - Press F12 if you haven't got the yakuake window open already and issue

```
rm ~/.irssi/config
```
then
```
nano ~/.irssi/config
```

and paste the following:

```
servers = (

  { address = "irc.SERVER1.com"; chatnet = "NETWORK1"; port = "6667"; },
  { address = "irc.SERVER2.com"; chatnet = "NETWORK2"; port = "6667"; },
  { address = "irc.SERVER3.com"; chatnet = "NETWORK3"; port = "6667"; },
  { address = "irc.SERVER4.com"; chatnet = "NETWORK4"; port = "6667"; },
);

chatnets = {
  NETWORK1 = {
    type = "IRC";
    nick = "YOURNICK";
    autosendcmd = "/^msg nickserv identify YOURPASS;wait 1000";
  };
  NETWORK2 = {
    type = "IRC";
    nick = "YOURNICK";
    autosendcmd = "/^msg nickserv identify YOURPASS;wait 1000";
  };
  NETWORK3 = {
    type = "IRC";
    nick = "YOURNICK";
    autosendcmd = "/^msg nickserv identify YOURPASS;wait 1000";
  };
  NETWORK4 = {
    type = "IRC";
    nick = "YOURNICK";
    autosendcmd = "/^msg nickserv identify YOURPASS;wait 1000";
  };

};

channels = (
  { name = "#CHANNEL1"; chatnet = "NETWORK1"; autojoin = "yes"; },
  { name = "#CHANNEL2"; chatnet = "NETWORK2"; autojoin = "yes"; },
  { name = "#CHANNEL3"; chatnet = "NETWORK3"; autojoin = "yes"; },
  { name = "#CHANNEL4"; chatnet = "NETWORK4"; autojoin = "yes"; },
);

aliases = {
  J = "join";
  WJOIN = "join -window";
  WQUERY = "query -window";
  LEAVE = "part";
  BYE = "quit";
  EXIT = "quit";
  SIGNOFF = "quit";
  DESCRIBE = "action";
  DATE = "time";
  HOST = "userhost";
  LAST = "lastlog";
  SAY = "msg *";
  WI = "whois";
  WII = "whois $0 $0";
  WW = "whowas";
  W = "who";
  N = "names";
  M = "msg";
  T = "topic";
  C = "clear";
  CL = "clear";
  K = "kick";
  KB = "kickban";
  KN = "knockout";
  BANS = "ban";
  B = "ban";
  MUB = "unban *";
  UB = "unban";
  IG = "ignore";
  UNIG = "unignore";
  SB = "scrollback";
  UMODE = "mode $N";
  WC = "window close";
  WN = "window new hide";
  SV = "say Irssi $J ($V) - http://irssi.org/";
  GOTO = "sb goto";
  CHAT = "dcc chat";
  RUN = "SCRIPT LOAD";
  UPTIME = "eval exec - expr `date +%s` - \\$F | awk '{print \"Irssi uptime: \"int(\\\\\\$1/3600/24)\"d \"int(\\\\\\$1/3600%24)\"h \"int(\\\\\\$1/60%60)\"m \"int(\\\\\\$1%60)\"s\" }'";
  CALC = "exec - if which bc &>/dev/null\\; then echo '$*' | bc | awk '{print \"$*=\"$$1}'\\; else echo bc was not found\\; fi";
  SBAR = "STATUSBAR";
  INVITELIST = "mode $C +I";
  Q = "QUERY";
  "MANUAL-WINDOWS" = "set use_status_window off;set autocreate_windows off;set autocreate_query_level none;set autoclose_windows off;set reuse_unused_windows on;save";
  EXEMPTLIST = "mode $C +e";
  ATAG = "WINDOW SERVER";
};

statusbar = {
  # formats:
  # when using {templates}, the template is shown only if it's argument isn't
  # empty unless no argument is given. for example {sb} is printed always,
  # but {sb $T} is printed only if $T isn't empty.

  items = {
    # start/end text in statusbars
    barstart = "{sbstart}";
    barend = "{sbend}";

    topicbarstart = "{topicsbstart}";
    topicbarend = "{topicsbend}";

    # treated "normally", you could change the time/user name to whatever
    time = "{sb $Z}";
    user = "{sb {sbnickmode $cumode}$N{sbmode $usermode}{sbaway $A}}";

    # treated specially .. window is printed with non-empty windows,
    # window_empty is printed with empty windows
    window = "{sb $winref:$itemname{sbmode $M}}";
    window_empty = "{sb $winref{sbservertag $tag}}";
    prompt = "{prompt $[.15]itemname}";
    prompt_empty = "{prompt $winname}";
    topic = " $topic";
    topic_empty = " Irssi v$J - http://irssi.org/help/";

    # all of these treated specially, they're only displayed when needed
    lag = "{sb Lag: $0-}";
    act = "{sb Act: $0-}";
    more = "-- more --";
  };

  # there's two type of statusbars. root statusbars are either at the top
  # of the screen or at the bottom of the screen. window statusbars are at
  # the top/bottom of each split window in screen.
  default = {
    # the "default statusbar" to be displayed at the bottom of the window.
    # contains all the normal items.
    window = {
      disabled = "no";

      # window, root
      type = "window";
      # top, bottom
      placement = "bottom";
      # number
      position = "1";
      # active, inactive, always
      visible = "active";

      # list of items in statusbar in the display order
      items = {
        barstart = { priority = "100"; };
        time = { };
        user = { };
        window = { };
        window_empty = { };
        lag = { priority = "-1"; };
        act = { priority = "10"; };
        more = { priority = "-1"; alignment = "right"; };
        barend = { priority = "100"; alignment = "right"; };
      };
    };

    # statusbar to use in inactive split windows
    window_inact = {
      type = "window";
      placement = "bottom";
      position = "1";
      visible = "inactive";
      items = {
        barstart = { priority = "100"; };
        window = { };
        window_empty = { };
        more = { priority = "-1"; alignment = "right"; };
        barend = { priority = "100"; alignment = "right"; };
      };
    };

    # we treat input line as yet another statusbar :) It's possible to
    # add other items before or after the input line item.
    prompt = {
      type = "root";
      placement = "bottom";
      # we want to be at the bottom always
      position = "100";
      visible = "always";
      items = {
        prompt = { priority = "-1"; };
        prompt_empty = { priority = "-1"; };
        # treated specially, this is the real input line.
        input = { priority = "10"; };
      };
    };

    # topicbar
    topic = {
      type = "root";
      placement = "top";
      position = "1";
      visible = "always";
      items = {
        topicbarstart = { priority = "100"; };
        topic = { };
        topic_empty = { };
        topicbarend = { priority = "100"; alignment = "right"; };
      };
    };
  };
};
settings = {
  core = {
    real_name = "User";
    user_name = "username";
    nick = "nickname";
  };
  "fe-common/core" = {
    autolog = "yes";
    autolog_path = "~/irclogs/$tag/$0.log";
  };
};
logs = { };

```

Replace SERVER1, NETWORK1, CHANNEL1, YOURNICK, YOURPASS etc. with your own preferences. If you don't use nickserv you can remove the "autosendcmd = "/^msg nickserv identify YOURPASS;wait 1000";" -lines. 
Press Ctrl-X, y, and Return/Enter to close nano and save the file.


Now that you've (hopefully) successfully configured irssi, issue "irssi" as a command in yakuake. Issue "/connect NETWORK1", "/connect NETWORK2" etc to connect to your networks. Once irssi is connected, press Ctrl-N to cycle to the next channel you've connected through in irssi.

Now finally, we come to root-tail

To install it, simply issue this command in your console:
```
sudo apt-get install root-tail
```

Now you'll want to configure root-tail. Personally I like to have it run automatically at start-up, but I'm using KDE through Kubuntu. If you're using KDE aswell, issue the following command:
```
nano ~/.kde/Autostart/root-tail
```

The nano text editor will open up. Copy-paste the following into it:

```
#!/bin/bash
/usr/bin/root-tail -g 800x250+50+50 -font '-misc-*-medium-r-*-*-10-*-*-*-*-*-iso8859-15' ~/irclogs/NETWORK1/\#CHANNEL1.log,green ~/irclogs/NETWORK2/\#CHANNEL2.log,white ~/irclogs/NETWORK3/\#CHANNEL3.log,red ~/irclogs/NETWORK4/\#CHANNEL4.log,yellow --reverse --justify --shade
```
Where NETWORK1 and CHANNEL1 etc. are the names of your IRC networks and channels as given in irssi. Press Ctrl-X, y, Return/Enter to close nano and save the file. Next issue this command:
```
chmod +x ~/.kde/Autostart/root-tail
```

The next time you log on, root-tail should be already started up. 

There is however one more thing you need to do before you can see root-tail's output in KDE; something Gnome users don't have to worry about. Right-click on your desktop and select Configure Desktop. Select Behavior amongst the column of icons to the left and mark "Allow programs in desktop window". Click OK, and now everything should be ready, unless I have forgotten something. To get root-tail running without logging on again, issue this command:

```
~/.kde/Autostart/root-tail
```

That's it. I hope you have, if not enjoyed, at least survived reading this guide. If you have any questions or problems, just reply and I'll try to do my best to answer in a timely manner. 

Links:
[http://irssi.org/](http://irssi.org/)
[http://www.goof.com/pcg/marc/root-tail.html](http://www.goof.com/pcg/marc/root-tail.html)
[http://gentoo-wiki.com/HOWTO_Autostart_Programs](http://gentoo-wiki.com/HOWTO_Autostart_Programs)

---

### Post by richieboy on 2007-07-05
do i have to start yakuake by hand or can i arrange to have it started at boot?  it seems silly to me to have to open a terminal to start a convenient terminal (yakuake).  it should just be there ready to go when i hit f12 or whatever trigger.

---

### Post by briguy on 2007-07-12
You don't have to start it by hand.  Put it in your .kde/Autostart folder.  The easiest way to do this is go into a terminal (yakuake will work well here) and type:

```
 ln -s /usr/bin/yakuake .
```

And it'll be up everytime you start.  Enjoy!

---

### Post by Nythain on 2007-07-12
you dont even have to put it in autostart... assuming you have kde set to re-use last session, and the fact that yakuake will still be running when you log out (its silly to quit it really) then it will automatically load on its own... now if ou dont have kde set to use last session then you will have to add the autostart entry

---


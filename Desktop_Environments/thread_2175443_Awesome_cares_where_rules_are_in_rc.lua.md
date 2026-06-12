---
title: "Awesome cares where rules are in rc.lua"
date: 2013-09-19
forum: Desktop Environments
---

### Post by Ranko Kohime on 2013-09-19
I've solved a rather perplexing issue, and now, if anyone knows why, I'd like to learn why Awesome behaves this way.

For my ease of editing, I moved the awful.rules.rules section from beneath the root.keys, up near the tags.  After this, a variety of key bindings no longer worked, such as Mod4+F, and Mod4+M, as two good examples.  My custom keybindings, such as for volume up/down, and screen locking continued to work fine, it was just a few of the default key bindings that suffered.  After moving awful.rules.rules back to it's former habitation, all of the key bindings work as they should.

Compare:

All working:
```
-- To find settings in this script, use the following index:
--
-- X.1 - Variable Definitions (default modkey, terminal, etc)
-- X.2 - Layout Definitions
-- X.3 - Tag Definitions & Client Rules
-- X.4
-- X.5
-- X.6

print("Debug: now loading gears: " .. os.time())
local gears = require("gears")          -- Standard awesome library
print("Debug: now loading awful: " .. os.time())
local awful = require("awful")          -- Standard awesome library
print("Debug: now loading awful.rules: " .. os.time())
awful.rules = require("awful.rules")        -- Standard awesome library
print("Debut: now loading tyranical: " .. os.time())
--local tyrannical = require("tyrannical")      -- Tyrannical dynamic tagging library
print("Debug: now loading awful.autofocus: " .. os.time())
require("awful.autofocus")              -- Standard awesome library
print("Debug: now loading wibox: " .. os.time())
local wibox = require("wibox")          -- Widget and layout library
print("Debug: now loading beautiful: " .. os.time())
local beautiful = require("beautiful")  -- Theme handling library
print("Debug: now loading naughty: " .. os.time())
local naughty = require("naughty")      -- Notification library
print("Debug: now loading menubar: " .. os.time())
local menubar = require("menubar")      -- Notification library
print("Debug: now loading volume: " .. os.time())

print("Debug: Began processing user rc.lua proper: " .. os.time())
-- {{{ Error handling
-- Check if awesome encountered an error during startup and fell back to
-- another config (This code will only ever execute for the fallback config)
if awesome.startup_errors then
    naughty.notify({ preset = naughty.config.presets.critical,
                     title = "Oops, there were errors during startup!",
                     text = awesome.startup_errors })
end

-- Handle runtime errors after startup
do
    local in_error = false
    awesome.connect_signal("debug::error", function (err)
        -- Make sure we don't go into an endless error loop
        if in_error then return end
        in_error = true

        naughty.notify({ preset = naughty.config.presets.critical,
                         title = "Oops, an error happened!",
                         text = err })
        in_error = false
    end)
end
-- }}}

-- Index X.1
-- {{{ Variable definitions
-- Themes define colours, icons, and wallpapers
beautiful.init("/home/ranko/Documents/Settings/awesome/themes/default/theme.lua")

-- This is used later as the default terminal and editor to run.
terminal = "urxvt"
editor = os.getenv("EDITOR") or "vi"
editor_cmd = terminal .. " -e " .. editor

-- Default modkey.
modkey = "Mod4"

-- Delightful widgets
--require('delightful.widgets.battery')
--require('delightful.widgets.cpu')
--require('delightful.widgets.datetime')
--require('delightful.widgets.imap')
--require('delightful.widgets.memory')
--require('delightful.widgets.network')
--require('delightful.widgets.pulseaudio')
--require('delightful.widgets.weather')


print("Debug: We're setting the wallpaper: " .. os.time())
-- {{{ Wallpaper
if beautiful.wallpaper then
    for s = 1, screen.count() do
        gears.wallpaper.maximized(beautiful.wallpaper, s, true)
    end
end
-- }}}

-- Index X.2
print("Debug: We're setting the layouts: " .. os.time())
-- Table of layouts to cover with awful.layout.inc, order matters.
local layouts =
{
    awful.layout.suit.tile.bottom,
    awful.layout.suit.tile.top,
    awful.layout.suit.tile.left,
    awful.layout.suit.tile,
    awful.layout.suit.max,
    awful.layout.suit.max.fullscreen,
    awful.layout.suit.magnifier,
    awful.layout.suit.floating
}
-- }}}

-- Disabled Layouts
--
--    awful.layout.suit.fair,
--    awful.layout.suit.fair.horizontal,
--    awful.layout.suit.spiral,
--    awful.layout.suit.spiral.dwindle,
--

-- Index X.3
print("Debug: We're setting up the tags: " .. os.time())
-- {{{ Tags
   -- Define a tag table which hold all screen tags.
tags = {}
for s = 1, screen.count() do
    -- Each screen has its own tag table.
  tags[s] = awful.tag({ "&#8984;", "&#9883;", "&#10009;", "&#9859;", "&#9890;", "&#26412;", "&#9881;" }, s, layouts[1] )
--  tags[s] = awful.tag({ "1", "2", "3", "4", "5", "6", "7" }, s, layouts[1] )
end
-- }}}



--tyrannical.tags = {
--    {
--        name        = " ",      -- Call the tag "Term"
--        init        = true,     -- Load the tag on startup
--        exclusive   = false,    -- Refuse any other type of clients (by classes)
--        icon        = "/home/ranko/.config/awesome/icons/1.png",
--        screen      = {1},       -- Create this tag on screen 1 and screen 2
--        clone_on    = {2,3,4,5}, -- Clone to other screens
--        selected    = true,     -- Selected when created (at awesome startup)
--        layout      = awful.layout.suit.tile.bottom,  -- Set layout
--        class       = { "org-gjt-sp-jedit-jEdit" }
--    } ,
--    {
--        name                = " ",      -- Internet
--        init                = true,
--        exclusive           = false,
--        nmaster             = 2,
--        no_focus_stealing   = true,
--        icon                = "/home/ranko/.config/awesome/icons/2.png",
--        screen              = {1},
--        clone_on            = {2,3,4,5},
--        layout              = awful.layout.suit.tile.bottom,
--        class               = { "google-chrome", "opera", "Thunderbird", "keepassx", "epiphany-browser", "midori", "jd", "xchat", }
--    },
--    {
--        name                = "&#10009; ",     -- Gaming
--        init                = true,
--        exclusive           = false,
--        nmaster             = 2,
--        no_focus_stealing   = true,
--        icon                = "/home/ranko/.config/awesome/icons/3.png",
--        screen              = {1},
--        layout              = awful.layout.suit.tile.top,
--        class               = { "Steam" }
--    },
--    {
--        name                = " ",      -- Video
--        init                = true,
--        exclusive           = false,
--        nmaster             = 2,
--        no_focus_stealing   = true,
--        icon                = "/home/ranko/.config/awesome/icons/4.png",
--        screen              = {1},
--        layout              = awful.layout.suit.tile.top,
--        class               = { "vlc", "umplayer" }
--    },
--    {
--        name                = " ",      -- Genealogy
--        init                = true,
--        exclusive           = false,
--        no_focus_stealing   = true,
--        mwfact              = 0.30,
--        icon                = "/home/ranko/.config/awesome/icons/5.png",
--        screen              = screen.count()>1 and 2 or 1,
--        layout              = awful.layout.suit.tile.top,
--        class               = { "Firefox" }
--    },
--    {
--        name                = " ",      -- Documentation
--        init                = true,
--        exclusive           = false,
--        nmaster             = 2,
--        no_focus_stealing   = true,
--        icon                = "/home/ranko/.config/awesome/icons/6.png",
--        screen              = screen.count()>1 and 2 or 1,
--        layout              = awful.layout.suit.tile.top,
--        class               = { "calibre-gui" }
--    },
--    {
--        name                = " ",      -- Wi-fi stumbling
--        init                = true,
--        exclusive           = false,
--        ncol                = 3,
--        nmaster             = 2,  
--        no_focus_stealing   = true,
--        icon                = "/home/ranko/.config/awesome/icons/7.png",
--        screen              = screen.count()>1 and 2 or 1,
--        layout              = awful.layout.suit.tile.top,
--        class               = { "Zenmap", "vinagre" }
--    }
--}
--tyrannical.properties.floating = {
--    "MPlayer" , "pinentry" , "pinentry" , "gtksu" , "xine" , "feh" , "xcalc" , "yakuake" , "Select Color$" , "Paste Special" , "New Form" , "Insert Picture" , "plasmoidviewer" , "TombRaider.exe" , "Portal2.exe" , "Steam" , "goldendict" , "clementine" , "unison-gtk" , 
--}
--tyrannical.properties.ontop = {
--    "Xephyr" , "ksnapshot" , "kruler" , "feh" , 
--    }
--tyrannical.properties.intrusive = {
--    "ksnapshot" , "pinentry" , "gtksu" , "kcalc" , "xcalc" , "feh" , "Gradient editor", "About KDE" , "Paste Special", "Background color" , "kcolorchooser" , "plasmoidviewer" , "Xephyr" , "kruler" , "plasmaengineexplorer" , "goldendict" , 
--    }
--tyrannical.properties.centered = {
--    "kcalc" , "pinentry" , "Xephyr" , "feh" , 
--    }
--tyrannical.properties.sticky = {
--    "clementine" ,
--    }
--
--    --Block popups ()
--tyrannical.settings.block_children_focus_stealing = false
--    --Force popups/dialogs to have the same tags as the parent client
--tyrannical.settings.group_children = true
--


-- {{{ Menu
-- Create a laucher widget and a main menu
myawesomemenu = {
   { "manual", terminal .. " -e man awesome" },
   { "edit config", editor_cmd .. " " .. awesome.conffile },
   { "restart", awesome.restart },
   { "quit", awesome.quit }
}

mymainmenu = awful.menu({ items = { { "awesome", myawesomemenu, beautiful.awesome_icon },
                                    { "open terminal", terminal }
                                  }
                        })

mylauncher = awful.widget.launcher({ image = beautiful.awesome_icon,
                                     menu = mymainmenu })

-- Menubar configuration
menubar.utils.terminal = terminal -- Set the terminal for applications that require it
-- }}}

-- {{{ Wibox
-- Create a textclock widget
mytextclock = awful.widget.textclock()

-- Create a wibox for each screen and add it
mywibox = {}
mypromptbox = {}
mylayoutbox = {}
mytaglist = {}
mytaglist.buttons = awful.util.table.join(
                    awful.button({ }, 1, awful.tag.viewonly),
                    awful.button({ modkey }, 1, awful.client.movetotag),
                    awful.button({ }, 3, awful.tag.viewtoggle),
                    awful.button({ modkey }, 3, awful.client.toggletag),
                    awful.button({ }, 4, function(t) awful.tag.viewnext(awful.tag.getscreen(t)) end),
                    awful.button({ }, 5, function(t) awful.tag.viewprev(awful.tag.getscreen(t)) end)
                    )
mytasklist = {}
mytasklist.buttons = awful.util.table.join(
                     awful.button({ }, 1, function (c)
                         if c == client.focus then
                             c.minimized = true
                         else
                             -- Without this, the following
                             -- :isvisible() makes no sense
                             c.minimized = false
                             if not c:isvisible() then
                                 awful.tag.viewonly(c:tags()[1])
                             end
                             -- This will also un-minimize
                             -- the client, if needed
                             client.focus = c
                             c:raise()
                         end
                     end),
                     awful.button({ }, 3, function ()
                                              if instance then
                                                  instance:hide()
                                                  instance = nil
                                              else
                                                  instance = awful.menu.clients({ width=250 })
                                              end
                                          end),
                     awful.button({ }, 4, function ()
                                              awful.client.focus.byidx(1)
                                              if client.focus then client.focus:raise() end
                                          end),
                     awful.button({ }, 5, function ()
                                              awful.client.focus.byidx(-1)
                                              if client.focus then client.focus:raise() end
                                          end))

for s = 1, screen.count() do
    -- Create a promptbox for each screen
    mypromptbox[s] = awful.widget.prompt()
    -- Create an imagebox widget which will contains an icon indicating which layout we're using.
    -- We need one layoutbox per screen.
    mylayoutbox[s] = awful.widget.layoutbox(s)
    mylayoutbox[s]:buttons(awful.util.table.join(
                           awful.button({ }, 1, function () awful.layout.inc(layouts, 1) end),
                           awful.button({ }, 3, function () awful.layout.inc(layouts, -1) end),
                           awful.button({ }, 4, function () awful.layout.inc(layouts, 1) end),
                           awful.button({ }, 5, function () awful.layout.inc(layouts, -1) end)))
    -- Create a taglist widget
    mytaglist[s] = awful.widget.taglist(s, awful.widget.taglist.filter.all, mytaglist.buttons)

    -- Create a tasklist widget
    mytasklist[s] = awful.widget.tasklist(s, awful.widget.tasklist.filter.currenttags, mytasklist.buttons)

    -- Create the wibox
    mywibox[s] = awful.wibox({ position = "top", screen = s })

    -- Widgets that are aligned to the left
    local left_layout = wibox.layout.fixed.horizontal()
    left_layout:add(mylauncher)
    left_layout:add(mylayoutbox[s])
    left_layout:add(mytaglist[s])
    left_layout:add(mypromptbox[s])

    -- Widgets that are aligned to the right
    local right_layout = wibox.layout.fixed.horizontal()
    if s == 1 then right_layout:add(wibox.widget.systray()) end
    right_layout:add(mytextclock)

    -- Now bring it all together (with the tasklist in the middle)
    local layout = wibox.layout.align.horizontal()
    layout:set_left(left_layout)
    layout:set_middle(mytasklist[s])
    layout:set_right(right_layout)

    mywibox[s]:set_widget(layout)
end
-- }}}

-- {{{ Mouse bindings
root.buttons(awful.util.table.join(
    awful.button({ }, 3, function () mymainmenu:toggle() end),
    awful.button({ }, 4, awful.tag.viewnext),
    awful.button({ }, 5, awful.tag.viewprev)
))
-- }}}

    print("Debug: Key Bindings: " .. os.time())
-- {{{ Key bindings

globalkeys = awful.util.table.join(
-- Custom Keys
  -- Volume Keys
        -- Laptop Keys
    awful.key({ }, "XF86AudioRaiseVolume",
      function ()
        awful.util.spawn("amixer set Master 5%+", false) end),
    awful.key({ }, "XF86AudioLowerVolume",
      function ()
        awful.util.spawn("amixer set Master 5%-", false) end),
    awful.key({ }, "XF86AudioMute",
      function ()
        awful.util.spawn("amixer sset Master toggle", false) end),
        -- External Keyboard
    awful.key({ modkey,         }, "F4",
      function ()
        awful.util.spawn("amixer set Master 5%+", false) end),
    awful.key({ modkey,         }, "F3",
      function ()
        awful.util.spawn("amixer set Master 5%-", false) end),
    awful.key({ modkey          }, "F2",
      function ()
        awful.util.spawn("amixer sset Master toggle", false) end),
  -- Other Custom Keys
    awful.key({modkey,      }, "F5",
      function ()
        awful.util.spawn("~/.screenlayout/internal.sh", false) end),
    awful.key({modkey,      }, "F6",
      function ()
        awful.util.spawn("~/.screenlayout/hdmi-768p-underscan.sh", false) end),
    awful.key({modkey,      }, "F7",
      function ()
        awful.util.spawn("~/.screenlayout/hdmi-1080p-underscan.sh", false) end),
    awful.key({modkey,      }, "F8",
      function ()
        awful.util.spawn("~/.screenlayout/hdmi-1080p-monitor.sh", false) end),
    awful.key({modkey,      }, "l",
      function ()
        awful.util.spawn("xscreensaver-command -lock", false) end),

    awful.key({ modkey,           }, "Left",   awful.tag.viewprev       ),
    awful.key({ modkey,           }, "Right",  awful.tag.viewnext       ),
    awful.key({ modkey,           }, "Escape", awful.tag.history.restore),
    awful.key({ modkey,           }, "j",
        function ()
            awful.client.focus.byidx( 1)
            if client.focus then client.focus:raise() end
        end),
    awful.key({ modkey,           }, "k",
        function ()
            awful.client.focus.byidx(-1)
            if client.focus then client.focus:raise() end
        end),
    awful.key({ modkey,           }, "w", function () mymainmenu:show() end),

    -- Layout manipulation
    awful.key({ modkey, "Shift"   }, "j", function () awful.client.swap.byidx(  1)    end),
    awful.key({ modkey, "Shift"   }, "k", function () awful.client.swap.byidx( -1)    end),
    awful.key({ modkey, "Control" }, "j", function () awful.screen.focus_relative( 1) end),
    awful.key({ modkey, "Control" }, "k", function () awful.screen.focus_relative(-1) end),
    awful.key({ modkey,           }, "u", awful.client.urgent.jumpto),
    awful.key({ modkey,           }, "Tab",
        function ()
            awful.client.focus.history.previous()
            if client.focus then
                client.focus:raise()
            end
        end),

    -- Standard program
    awful.key({ modkey,           }, "Return", function () awful.util.spawn(terminal) end),
    awful.key({ modkey, "Control" }, "r", awesome.restart),
    awful.key({ modkey, "Shift"   }, "q", awesome.quit),

    awful.key({ modkey,           }, "l",     function () awful.tag.incmwfact( 0.05)    end),
    awful.key({ modkey,           }, "h",     function () awful.tag.incmwfact(-0.05)    end),
    awful.key({ modkey, "Shift"   }, "h",     function () awful.tag.incnmaster( 1)      end),
    awful.key({ modkey, "Shift"   }, "l",     function () awful.tag.incnmaster(-1)      end),
    awful.key({ modkey, "Control" }, "h",     function () awful.tag.incncol( 1)         end),
    awful.key({ modkey, "Control" }, "l",     function () awful.tag.incncol(-1)         end),
    awful.key({ modkey,           }, "space", function () awful.layout.inc(layouts,  1) end),
    awful.key({ modkey, "Shift"   }, "space", function () awful.layout.inc(layouts, -1) end),

    awful.key({ modkey, "Control" }, "n", awful.client.restore),

    -- Prompt
    awful.key({ modkey },            "r",     function () mypromptbox[mouse.screen]:run() end),

    awful.key({ modkey }, "x",
              function ()
                  awful.prompt.run({ prompt = "Run Lua code: " },
                  mypromptbox[mouse.screen].widget,
                  awful.util.eval, nil,
                  awful.util.getdir("cache") .. "/history_eval")
              end),
    -- Menubar
    awful.key({ modkey }, "p", function() menubar.show() end)
)

clientkeys = awful.util.table.join(
    awful.key({ modkey,           }, "f",      function (c) c.fullscreen = not c.fullscreen  end),
    awful.key({ modkey, "Shift"   }, "c",      function (c) c:kill()                         end),
    awful.key({ modkey, "Control" }, "space",  awful.client.floating.toggle                     ),
    awful.key({ modkey, "Control" }, "Return", function (c) c:swap(awful.client.getmaster()) end),
    awful.key({ modkey,           }, "o",      awful.client.movetoscreen                        ),
    awful.key({ modkey,           }, "t",      function (c) c.ontop = not c.ontop            end),
    awful.key({ modkey,           }, "n",
        function (c)
            -- The client currently has the input focus, so it cannot be
            -- minimized, since minimized clients can't have the focus.
            c.minimized = true
        end),
    awful.key({ modkey,           }, "m",
        function (c)
            c.maximized_horizontal = not c.maximized_horizontal
            c.maximized_vertical   = not c.maximized_vertical
        end)
)

-- Bind all key numbers to tags.
-- Be careful: we use keycodes to make it works on any keyboard layout.
-- This should map on the top row of your keyboard, usually 1 to 9.
for i = 1, 9 do
    globalkeys = awful.util.table.join(globalkeys,
        awful.key({ modkey }, "#" .. i + 9,
                  function ()
                        local screen = mouse.screen
                        local tag = awful.tag.gettags(screen)[i]
                        if tag then
                           awful.tag.viewonly(tag)
                        end
                  end),
        awful.key({ modkey, "Control" }, "#" .. i + 9,
                  function ()
                      local screen = mouse.screen
                      local tag = awful.tag.gettags(screen)[i]
                      if tag then
                         awful.tag.viewtoggle(tag)
                      end
                  end),
        awful.key({ modkey, "Shift" }, "#" .. i + 9,
                  function ()
                      local tag = awful.tag.gettags(client.focus.screen)[i]
                      if client.focus and tag then
                          awful.client.movetotag(tag)
                     end
                  end),
        awful.key({ modkey, "Control", "Shift" }, "#" .. i + 9,
                  function ()
                      local tag = awful.tag.gettags(client.focus.screen)[i]
                      if client.focus and tag then
                          awful.client.toggletag(tag)
                      end
                  end))
end

clientbuttons = awful.util.table.join(
    awful.button({ }, 1, function (c) client.focus = c; c:raise() end),
    awful.button({ modkey }, 1, awful.mouse.client.move),
    awful.button({ modkey }, 3, awful.mouse.client.resize))

-- Set keys
root.keys(globalkeys)
-- }}}

-- {{{ Rules
awful.rules.rules = {
  -- All clients will match this rule.
  { rule = { },
    properties = { border_width = beautiful.border_width,
                   border_color = beautiful.border_normal,
                   focus = awful.client.focus.filter,
                   keys = clientkeys,
                   buttons = clientbuttons } },
  { rule = { class = "MPlayer" }, properties = { floating = true } },
  { rule = { class = "pinentry" }, properties = { floating = true } },
  { rule = { class = "gimp" }, properties = { floating = true } },

  { rule = { class = "Orage" }, properties = { floating = true } },
  { rule = { class = "Skype" }, properties = { floating = true } },
  { rule = { class = "Clementine" }, properties = { sticky = true } },

-- Tag 1
--  { rule = { class = "org-gjt-sp-jedit-jEdit" }, properties = { tag = tags[1][1] } },
-- Tag 2
  { rule = { class = "google-chrome" }, properties = { tag = tags[1][2] } },
  { rule = { class = "opera" }, properties = { tag = tags[1][2] } },
  { rule = { class = "Thunderbird" }, properties = { tag = tags[1][2] } },
  { rule = { class = "keepassx" }, properties = { tag = tags[1][2] } },
  { rule = { class = "epiphany-browser" }, properties = { tag = tags[1][2] } },
  { rule = { class = "midori" }, properties = { tag = tags[1][2] } },
  { rule = { class = "jd" }, properties = { tag = tags[1][2] } },
  { rule = { class = "xchat" }, properties = { tag = tags[1][2] } },
-- Tag 3
  { rule = { class = "Steam" }, properties = { tag = tags[1][3] } },
  { rule = { class = "Desura" }, properties = { tag = tags[1][3] } },
  { rule = { name = "Analogue: A Hate Story" },
    properties = { tag = tags[1][3] },
      { floating = true }
  },
-- Tag 4
  { rule = { class = "umplayer" }, properties = { tag = tags[1][4] } },
  { rule = { class = "vlc" }, properties = { tag = tags[1][4] } },
-- Tag 5
  { rule = { class = "Firefox" }, properties = { tag = tags[1][5] } },
  { rule = { name = "/home/ranko/Documents/Genealogy/(1980) The Vining Family.pdf" }, properties = { tag = tags[1][5] } },
-- Tag 6
  { rule = { class = "calibre-gui" }, properties = { tag = tags[1][6] } },
-- Tag 7
  { rule = { class = "Zenmap" }, properties = { tag = tags[1][7] } },
  { rule = { class = "vinagre" }, properties = { tag = tags[1][7] } },

}
-- }}}


-- {{{ Signals
-- Signal function to execute when a new client appears.
client.connect_signal("manage", function (c, startup)
    -- Enable sloppy focus
    c:connect_signal("mouse::enter", function(c)
        if awful.layout.get(c.screen) ~= awful.layout.suit.magnifier
            and awful.client.focus.filter(c) then
            client.focus = c
        end
    end)

    if not startup then
        -- Set the windows at the slave,
        -- i.e. put it at the end of others instead of setting it master.
        -- awful.client.setslave(c)

        -- Put windows in a smart way, only if they does not set an initial position.
        if not c.size_hints.user_position and not c.size_hints.program_position then
            awful.placement.no_overlap(c)
            awful.placement.no_offscreen(c)
        end
    end

    local titlebars_enabled = false
    if titlebars_enabled and (c.type == "normal" or c.type == "dialog") then
        -- buttons for the titlebar
        local buttons = awful.util.table.join(
                awful.button({ }, 1, function()
                    client.focus = c
                    c:raise()
                    awful.mouse.client.move(c)
                end),
                awful.button({ }, 3, function()
                    client.focus = c
                    c:raise()
                    awful.mouse.client.resize(c)
                end)
                )

        -- Widgets that are aligned to the left
        local left_layout = wibox.layout.fixed.horizontal()
        left_layout:add(awful.titlebar.widget.iconwidget(c))
        left_layout:buttons(buttons)

        -- Widgets that are aligned to the right
        local right_layout = wibox.layout.fixed.horizontal()
        right_layout:add(awful.titlebar.widget.floatingbutton(c))
        right_layout:add(awful.titlebar.widget.maximizedbutton(c))
        right_layout:add(awful.titlebar.widget.stickybutton(c))
        right_layout:add(awful.titlebar.widget.ontopbutton(c))
        right_layout:add(awful.titlebar.widget.closebutton(c))

        -- The title goes in the middle
        local middle_layout = wibox.layout.flex.horizontal()
        local title = awful.titlebar.widget.titlewidget(c)
        title:set_align("center")
        middle_layout:add(title)
        middle_layout:buttons(buttons)

        -- Now bring it all together
        local layout = wibox.layout.align.horizontal()
        layout:set_left(left_layout)
        layout:set_right(right_layout)
        layout:set_middle(middle_layout)

        awful.titlebar(c):set_widget(layout)
    end
end)

client.connect_signal("focus", function(c) c.border_color = beautiful.border_focus end)
client.connect_signal("unfocus", function(c) c.border_color = beautiful.border_normal end)
-- }}}
```

To some, not so much:
```
-- To find settings in this script, use the following index:
--
-- X.1 - Variable Definitions (default modkey, terminal, etc)
-- X.2 - Layout Definitions
-- X.3 - Tag Definitions & Client Rules
-- X.4
-- X.5
-- X.6

print("Debug: now loading gears: " .. os.time())
local gears = require("gears")          -- Standard awesome library
print("Debug: now loading awful: " .. os.time())
local awful = require("awful")          -- Standard awesome library
print("Debug: now loading awful.rules: " .. os.time())
awful.rules = require("awful.rules")        -- Standard awesome library
print("Debut: now loading tyranical: " .. os.time())
--local tyrannical = require("tyrannical")      -- Tyrannical dynamic tagging library
print("Debug: now loading awful.autofocus: " .. os.time())
require("awful.autofocus")              -- Standard awesome library
print("Debug: now loading wibox: " .. os.time())
local wibox = require("wibox")          -- Widget and layout library
print("Debug: now loading beautiful: " .. os.time())
local beautiful = require("beautiful")  -- Theme handling library
print("Debug: now loading naughty: " .. os.time())
local naughty = require("naughty")      -- Notification library
print("Debug: now loading menubar: " .. os.time())
local menubar = require("menubar")      -- Notification library
print("Debug: now loading volume: " .. os.time())

print("Debug: Began processing user rc.lua proper: " .. os.time())
-- {{{ Error handling
-- Check if awesome encountered an error during startup and fell back to
-- another config (This code will only ever execute for the fallback config)
if awesome.startup_errors then
    naughty.notify({ preset = naughty.config.presets.critical,
                     title = "Oops, there were errors during startup!",
                     text = awesome.startup_errors })
end

-- Handle runtime errors after startup
do
    local in_error = false
    awesome.connect_signal("debug::error", function (err)
        -- Make sure we don't go into an endless error loop
        if in_error then return end
        in_error = true

        naughty.notify({ preset = naughty.config.presets.critical,
                         title = "Oops, an error happened!",
                         text = err })
        in_error = false
    end)
end
-- }}}

-- Index X.1
-- {{{ Variable definitions
-- Themes define colours, icons, and wallpapers
beautiful.init("/home/ranko/Documents/Settings/awesome/themes/default/theme.lua")

-- This is used later as the default terminal and editor to run.
terminal = "urxvt"
editor = os.getenv("EDITOR") or "vi"
editor_cmd = terminal .. " -e " .. editor

-- Default modkey.
modkey = "Mod4"

-- Delightful widgets
--require('delightful.widgets.battery')
--require('delightful.widgets.cpu')
--require('delightful.widgets.datetime')
--require('delightful.widgets.imap')
--require('delightful.widgets.memory')
--require('delightful.widgets.network')
--require('delightful.widgets.pulseaudio')
--require('delightful.widgets.weather')


print("Debug: We're setting the wallpaper: " .. os.time())
-- {{{ Wallpaper
if beautiful.wallpaper then
    for s = 1, screen.count() do
        gears.wallpaper.maximized(beautiful.wallpaper, s, true)
    end
end
-- }}}

-- Index X.2
print("Debug: We're setting the layouts: " .. os.time())
-- Table of layouts to cover with awful.layout.inc, order matters.
local layouts =
{
    awful.layout.suit.tile.bottom,
    awful.layout.suit.tile.top,
    awful.layout.suit.tile.left,
    awful.layout.suit.tile,
    awful.layout.suit.max,
    awful.layout.suit.max.fullscreen,
    awful.layout.suit.magnifier,
    awful.layout.suit.floating
}
-- }}}

-- Disabled Layouts
--
--    awful.layout.suit.fair,
--    awful.layout.suit.fair.horizontal,
--    awful.layout.suit.spiral,
--    awful.layout.suit.spiral.dwindle,
--

-- Index X.3
print("Debug: We're setting up the tags: " .. os.time())
-- {{{ Tags
   -- Define a tag table which hold all screen tags.
tags = {}
for s = 1, screen.count() do
    -- Each screen has its own tag table.
  tags[s] = awful.tag({ "&#8984;", "&#9883;", "&#10009;", "&#9859;", "&#9890;", "&#26412;", "&#9881;" }, s, layouts[1] )
--  tags[s] = awful.tag({ "1", "2", "3", "4", "5", "6", "7" }, s, layouts[1] )
end
-- }}}

-- {{{ Rules
awful.rules.rules = {
  -- All clients will match this rule.
  { rule = { },
    properties = { border_width = beautiful.border_width,
                   border_color = beautiful.border_normal,
                   focus = awful.client.focus.filter,
                   keys = clientkeys,
                   buttons = clientbuttons } },
  { rule = { class = "MPlayer" }, properties = { floating = true } },
  { rule = { class = "pinentry" }, properties = { floating = true } },
  { rule = { class = "gimp" }, properties = { floating = true } },

  { rule = { class = "Orage" }, properties = { floating = true } },
  { rule = { class = "Skype" }, properties = { floating = true } },
  { rule = { class = "Clementine" }, properties = { sticky = true } },

-- Tag 1
--  { rule = { class = "org-gjt-sp-jedit-jEdit" }, properties = { tag = tags[1][1] } },
-- Tag 2
  { rule = { class = "google-chrome" }, properties = { tag = tags[1][2] } },
  { rule = { class = "opera" }, properties = { tag = tags[1][2] } },
  { rule = { class = "Thunderbird" }, properties = { tag = tags[1][2] } },
  { rule = { class = "keepassx" }, properties = { tag = tags[1][2] } },
  { rule = { class = "epiphany-browser" }, properties = { tag = tags[1][2] } },
  { rule = { class = "midori" }, properties = { tag = tags[1][2] } },
  { rule = { class = "jd" }, properties = { tag = tags[1][2] } },
  { rule = { class = "xchat" }, properties = { tag = tags[1][2] } },
-- Tag 3
  { rule = { class = "Steam" }, properties = { tag = tags[1][3] } },
  { rule = { class = "Desura" }, properties = { tag = tags[1][3] } },
  { rule = { name = "Analogue: A Hate Story" },
    properties = { tag = tags[1][3] },
      { floating = true }
  },
-- Tag 4
  { rule = { class = "umplayer" }, properties = { tag = tags[1][4] } },
  { rule = { class = "vlc" }, properties = { tag = tags[1][4] } },
-- Tag 5
  { rule = { class = "Firefox" }, properties = { tag = tags[1][5] } },
  { rule = { name = "/home/ranko/Documents/Genealogy/(1980) The Vining Family.pdf" }, properties = { tag = tags[1][5] } },
-- Tag 6
  { rule = { class = "calibre-gui" }, properties = { tag = tags[1][6] } },
-- Tag 7
  { rule = { class = "Zenmap" }, properties = { tag = tags[1][7] } },
  { rule = { class = "vinagre" }, properties = { tag = tags[1][7] } },

}
-- }}}


--tyrannical.tags = {
--    {
--        name        = " ",      -- Call the tag "Term"
--        init        = true,     -- Load the tag on startup
--        exclusive   = false,    -- Refuse any other type of clients (by classes)
--        icon        = "/home/ranko/.config/awesome/icons/1.png",
--        screen      = {1},       -- Create this tag on screen 1 and screen 2
--        clone_on    = {2,3,4,5}, -- Clone to other screens
--        selected    = true,     -- Selected when created (at awesome startup)
--        layout      = awful.layout.suit.tile.bottom,  -- Set layout
--        class       = { "org-gjt-sp-jedit-jEdit" }
--    } ,
--    {
--        name                = " ",      -- Internet
--        init                = true,
--        exclusive           = false,
--        nmaster             = 2,
--        no_focus_stealing   = true,
--        icon                = "/home/ranko/.config/awesome/icons/2.png",
--        screen              = {1},
--        clone_on            = {2,3,4,5},
--        layout              = awful.layout.suit.tile.bottom,
--        class               = { "google-chrome", "opera", "Thunderbird", "keepassx", "epiphany-browser", "midori", "jd", "xchat", }
--    },
--    {
--        name                = "&#10009; ",     -- Gaming
--        init                = true,
--        exclusive           = false,
--        nmaster             = 2,
--        no_focus_stealing   = true,
--        icon                = "/home/ranko/.config/awesome/icons/3.png",
--        screen              = {1},
--        layout              = awful.layout.suit.tile.top,
--        class               = { "Steam" }
--    },
--    {
--        name                = " ",      -- Video
--        init                = true,
--        exclusive           = false,
--        nmaster             = 2,
--        no_focus_stealing   = true,
--        icon                = "/home/ranko/.config/awesome/icons/4.png",
--        screen              = {1},
--        layout              = awful.layout.suit.tile.top,
--        class               = { "vlc", "umplayer" }
--    },
--    {
--        name                = " ",      -- Genealogy
--        init                = true,
--        exclusive           = false,
--        no_focus_stealing   = true,
--        mwfact              = 0.30,
--        icon                = "/home/ranko/.config/awesome/icons/5.png",
--        screen              = screen.count()>1 and 2 or 1,
--        layout              = awful.layout.suit.tile.top,
--        class               = { "Firefox" }
--    },
--    {
--        name                = " ",      -- Documentation
--        init                = true,
--        exclusive           = false,
--        nmaster             = 2,
--        no_focus_stealing   = true,
--        icon                = "/home/ranko/.config/awesome/icons/6.png",
--        screen              = screen.count()>1 and 2 or 1,
--        layout              = awful.layout.suit.tile.top,
--        class               = { "calibre-gui" }
--    },
--    {
--        name                = " ",      -- Wi-fi stumbling
--        init                = true,
--        exclusive           = false,
--        ncol                = 3,
--        nmaster             = 2,  
--        no_focus_stealing   = true,
--        icon                = "/home/ranko/.config/awesome/icons/7.png",
--        screen              = screen.count()>1 and 2 or 1,
--        layout              = awful.layout.suit.tile.top,
--        class               = { "Zenmap", "vinagre" }
--    }
--}
--tyrannical.properties.floating = {
--    "MPlayer" , "pinentry" , "pinentry" , "gtksu" , "xine" , "feh" , "xcalc" , "yakuake" , "Select Color$" , "Paste Special" , "New Form" , "Insert Picture" , "plasmoidviewer" , "TombRaider.exe" , "Portal2.exe" , "Steam" , "goldendict" , "clementine" , "unison-gtk" , 
--}
--tyrannical.properties.ontop = {
--    "Xephyr" , "ksnapshot" , "kruler" , "feh" , 
--    }
--tyrannical.properties.intrusive = {
--    "ksnapshot" , "pinentry" , "gtksu" , "kcalc" , "xcalc" , "feh" , "Gradient editor", "About KDE" , "Paste Special", "Background color" , "kcolorchooser" , "plasmoidviewer" , "Xephyr" , "kruler" , "plasmaengineexplorer" , "goldendict" , 
--    }
--tyrannical.properties.centered = {
--    "kcalc" , "pinentry" , "Xephyr" , "feh" , 
--    }
--tyrannical.properties.sticky = {
--    "clementine" ,
--    }
--
--    --Block popups ()
--tyrannical.settings.block_children_focus_stealing = false
--    --Force popups/dialogs to have the same tags as the parent client
--tyrannical.settings.group_children = true
--


-- {{{ Menu
-- Create a laucher widget and a main menu
myawesomemenu = {
   { "manual", terminal .. " -e man awesome" },
   { "edit config", editor_cmd .. " " .. awesome.conffile },
   { "restart", awesome.restart },
   { "quit", awesome.quit }
}

mymainmenu = awful.menu({ items = { { "awesome", myawesomemenu, beautiful.awesome_icon },
                                    { "open terminal", terminal }
                                  }
                        })

mylauncher = awful.widget.launcher({ image = beautiful.awesome_icon,
                                     menu = mymainmenu })

-- Menubar configuration
menubar.utils.terminal = terminal -- Set the terminal for applications that require it
-- }}}

-- {{{ Wibox
-- Create a textclock widget
mytextclock = awful.widget.textclock()

-- Create a wibox for each screen and add it
mywibox = {}
mypromptbox = {}
mylayoutbox = {}
mytaglist = {}
mytaglist.buttons = awful.util.table.join(
                    awful.button({ }, 1, awful.tag.viewonly),
                    awful.button({ modkey }, 1, awful.client.movetotag),
                    awful.button({ }, 3, awful.tag.viewtoggle),
                    awful.button({ modkey }, 3, awful.client.toggletag),
                    awful.button({ }, 4, function(t) awful.tag.viewnext(awful.tag.getscreen(t)) end),
                    awful.button({ }, 5, function(t) awful.tag.viewprev(awful.tag.getscreen(t)) end)
                    )
mytasklist = {}
mytasklist.buttons = awful.util.table.join(
                     awful.button({ }, 1, function (c)
                         if c == client.focus then
                             c.minimized = true
                         else
                             -- Without this, the following
                             -- :isvisible() makes no sense
                             c.minimized = false
                             if not c:isvisible() then
                                 awful.tag.viewonly(c:tags()[1])
                             end
                             -- This will also un-minimize
                             -- the client, if needed
                             client.focus = c
                             c:raise()
                         end
                     end),
                     awful.button({ }, 3, function ()
                                              if instance then
                                                  instance:hide()
                                                  instance = nil
                                              else
                                                  instance = awful.menu.clients({ width=250 })
                                              end
                                          end),
                     awful.button({ }, 4, function ()
                                              awful.client.focus.byidx(1)
                                              if client.focus then client.focus:raise() end
                                          end),
                     awful.button({ }, 5, function ()
                                              awful.client.focus.byidx(-1)
                                              if client.focus then client.focus:raise() end
                                          end))

for s = 1, screen.count() do
    -- Create a promptbox for each screen
    mypromptbox[s] = awful.widget.prompt()
    -- Create an imagebox widget which will contains an icon indicating which layout we're using.
    -- We need one layoutbox per screen.
    mylayoutbox[s] = awful.widget.layoutbox(s)
    mylayoutbox[s]:buttons(awful.util.table.join(
                           awful.button({ }, 1, function () awful.layout.inc(layouts, 1) end),
                           awful.button({ }, 3, function () awful.layout.inc(layouts, -1) end),
                           awful.button({ }, 4, function () awful.layout.inc(layouts, 1) end),
                           awful.button({ }, 5, function () awful.layout.inc(layouts, -1) end)))
    -- Create a taglist widget
    mytaglist[s] = awful.widget.taglist(s, awful.widget.taglist.filter.all, mytaglist.buttons)

    -- Create a tasklist widget
    mytasklist[s] = awful.widget.tasklist(s, awful.widget.tasklist.filter.currenttags, mytasklist.buttons)

    -- Create the wibox
    mywibox[s] = awful.wibox({ position = "top", screen = s })

    -- Widgets that are aligned to the left
    local left_layout = wibox.layout.fixed.horizontal()
    left_layout:add(mylauncher)
    left_layout:add(mylayoutbox[s])
    left_layout:add(mytaglist[s])
    left_layout:add(mypromptbox[s])

    -- Widgets that are aligned to the right
    local right_layout = wibox.layout.fixed.horizontal()
    if s == 1 then right_layout:add(wibox.widget.systray()) end
    right_layout:add(mytextclock)

    -- Now bring it all together (with the tasklist in the middle)
    local layout = wibox.layout.align.horizontal()
    layout:set_left(left_layout)
    layout:set_middle(mytasklist[s])
    layout:set_right(right_layout)

    mywibox[s]:set_widget(layout)
end
-- }}}

-- {{{ Mouse bindings
root.buttons(awful.util.table.join(
    awful.button({ }, 3, function () mymainmenu:toggle() end),
    awful.button({ }, 4, awful.tag.viewnext),
    awful.button({ }, 5, awful.tag.viewprev)
))
-- }}}

    print("Debug: Key Bindings: " .. os.time())
-- {{{ Key bindings

globalkeys = awful.util.table.join(
-- Custom Keys
  -- Volume Keys
        -- Laptop Keys
    awful.key({ }, "XF86AudioRaiseVolume",
      function ()
        awful.util.spawn("amixer set Master 5%+", false) end),
    awful.key({ }, "XF86AudioLowerVolume",
      function ()
        awful.util.spawn("amixer set Master 5%-", false) end),
    awful.key({ }, "XF86AudioMute",
      function ()
        awful.util.spawn("amixer sset Master toggle", false) end),
        -- External Keyboard
    awful.key({ modkey,         }, "F4",
      function ()
        awful.util.spawn("amixer set Master 5%+", false) end),
    awful.key({ modkey,         }, "F3",
      function ()
        awful.util.spawn("amixer set Master 5%-", false) end),
    awful.key({ modkey          }, "F2",
      function ()
        awful.util.spawn("amixer sset Master toggle", false) end),
  -- Other Custom Keys
    awful.key({modkey,      }, "F5",
      function ()
        awful.util.spawn("~/.screenlayout/internal.sh", false) end),
    awful.key({modkey,      }, "F6",
      function ()
        awful.util.spawn("~/.screenlayout/hdmi-768p-underscan.sh", false) end),
    awful.key({modkey,      }, "F7",
      function ()
        awful.util.spawn("~/.screenlayout/hdmi-1080p-underscan.sh", false) end),
    awful.key({modkey,      }, "F8",
      function ()
        awful.util.spawn("~/.screenlayout/hdmi-1080p-monitor.sh", false) end),
    awful.key({modkey,      }, "l",
      function ()
        awful.util.spawn("xscreensaver-command -lock", false) end),

    awful.key({ modkey,           }, "Left",   awful.tag.viewprev       ),
    awful.key({ modkey,           }, "Right",  awful.tag.viewnext       ),
    awful.key({ modkey,           }, "Escape", awful.tag.history.restore),
    awful.key({ modkey,           }, "j",
        function ()
            awful.client.focus.byidx( 1)
            if client.focus then client.focus:raise() end
        end),
    awful.key({ modkey,           }, "k",
        function ()
            awful.client.focus.byidx(-1)
            if client.focus then client.focus:raise() end
        end),
    awful.key({ modkey,           }, "w", function () mymainmenu:show() end),

    -- Layout manipulation
    awful.key({ modkey, "Shift"   }, "j", function () awful.client.swap.byidx(  1)    end),
    awful.key({ modkey, "Shift"   }, "k", function () awful.client.swap.byidx( -1)    end),
    awful.key({ modkey, "Control" }, "j", function () awful.screen.focus_relative( 1) end),
    awful.key({ modkey, "Control" }, "k", function () awful.screen.focus_relative(-1) end),
    awful.key({ modkey,           }, "u", awful.client.urgent.jumpto),
    awful.key({ modkey,           }, "Tab",
        function ()
            awful.client.focus.history.previous()
            if client.focus then
                client.focus:raise()
            end
        end),

    -- Standard program
    awful.key({ modkey,           }, "Return", function () awful.util.spawn(terminal) end),
    awful.key({ modkey, "Control" }, "r", awesome.restart),
    awful.key({ modkey, "Shift"   }, "q", awesome.quit),

    awful.key({ modkey,           }, "l",     function () awful.tag.incmwfact( 0.05)    end),
    awful.key({ modkey,           }, "h",     function () awful.tag.incmwfact(-0.05)    end),
    awful.key({ modkey, "Shift"   }, "h",     function () awful.tag.incnmaster( 1)      end),
    awful.key({ modkey, "Shift"   }, "l",     function () awful.tag.incnmaster(-1)      end),
    awful.key({ modkey, "Control" }, "h",     function () awful.tag.incncol( 1)         end),
    awful.key({ modkey, "Control" }, "l",     function () awful.tag.incncol(-1)         end),
    awful.key({ modkey,           }, "space", function () awful.layout.inc(layouts,  1) end),
    awful.key({ modkey, "Shift"   }, "space", function () awful.layout.inc(layouts, -1) end),

    awful.key({ modkey, "Control" }, "n", awful.client.restore),

    -- Prompt
    awful.key({ modkey },            "r",     function () mypromptbox[mouse.screen]:run() end),

    awful.key({ modkey }, "x",
              function ()
                  awful.prompt.run({ prompt = "Run Lua code: " },
                  mypromptbox[mouse.screen].widget,
                  awful.util.eval, nil,
                  awful.util.getdir("cache") .. "/history_eval")
              end),
    -- Menubar
    awful.key({ modkey }, "p", function() menubar.show() end)
)

clientkeys = awful.util.table.join(
    awful.key({ modkey,           }, "f",      function (c) c.fullscreen = not c.fullscreen  end),
    awful.key({ modkey, "Shift"   }, "c",      function (c) c:kill()                         end),
    awful.key({ modkey, "Control" }, "space",  awful.client.floating.toggle                     ),
    awful.key({ modkey, "Control" }, "Return", function (c) c:swap(awful.client.getmaster()) end),
    awful.key({ modkey,           }, "o",      awful.client.movetoscreen                        ),
    awful.key({ modkey,           }, "t",      function (c) c.ontop = not c.ontop            end),
    awful.key({ modkey,           }, "n",
        function (c)
            -- The client currently has the input focus, so it cannot be
            -- minimized, since minimized clients can't have the focus.
            c.minimized = true
        end),
    awful.key({ modkey,           }, "m",
        function (c)
            c.maximized_horizontal = not c.maximized_horizontal
            c.maximized_vertical   = not c.maximized_vertical
        end)
)

-- Bind all key numbers to tags.
-- Be careful: we use keycodes to make it works on any keyboard layout.
-- This should map on the top row of your keyboard, usually 1 to 9.
for i = 1, 9 do
    globalkeys = awful.util.table.join(globalkeys,
        awful.key({ modkey }, "#" .. i + 9,
                  function ()
                        local screen = mouse.screen
                        local tag = awful.tag.gettags(screen)[i]
                        if tag then
                           awful.tag.viewonly(tag)
                        end
                  end),
        awful.key({ modkey, "Control" }, "#" .. i + 9,
                  function ()
                      local screen = mouse.screen
                      local tag = awful.tag.gettags(screen)[i]
                      if tag then
                         awful.tag.viewtoggle(tag)
                      end
                  end),
        awful.key({ modkey, "Shift" }, "#" .. i + 9,
                  function ()
                      local tag = awful.tag.gettags(client.focus.screen)[i]
                      if client.focus and tag then
                          awful.client.movetotag(tag)
                     end
                  end),
        awful.key({ modkey, "Control", "Shift" }, "#" .. i + 9,
                  function ()
                      local tag = awful.tag.gettags(client.focus.screen)[i]
                      if client.focus and tag then
                          awful.client.toggletag(tag)
                      end
                  end))
end

clientbuttons = awful.util.table.join(
    awful.button({ }, 1, function (c) client.focus = c; c:raise() end),
    awful.button({ modkey }, 1, awful.mouse.client.move),
    awful.button({ modkey }, 3, awful.mouse.client.resize))

-- Set keys
root.keys(globalkeys)
-- }}}



-- {{{ Signals
-- Signal function to execute when a new client appears.
client.connect_signal("manage", function (c, startup)
    -- Enable sloppy focus
    c:connect_signal("mouse::enter", function(c)
        if awful.layout.get(c.screen) ~= awful.layout.suit.magnifier
            and awful.client.focus.filter(c) then
            client.focus = c
        end
    end)

    if not startup then
        -- Set the windows at the slave,
        -- i.e. put it at the end of others instead of setting it master.
        -- awful.client.setslave(c)

        -- Put windows in a smart way, only if they does not set an initial position.
        if not c.size_hints.user_position and not c.size_hints.program_position then
            awful.placement.no_overlap(c)
            awful.placement.no_offscreen(c)
        end
    end

    local titlebars_enabled = false
    if titlebars_enabled and (c.type == "normal" or c.type == "dialog") then
        -- buttons for the titlebar
        local buttons = awful.util.table.join(
                awful.button({ }, 1, function()
                    client.focus = c
                    c:raise()
                    awful.mouse.client.move(c)
                end),
                awful.button({ }, 3, function()
                    client.focus = c
                    c:raise()
                    awful.mouse.client.resize(c)
                end)
                )

        -- Widgets that are aligned to the left
        local left_layout = wibox.layout.fixed.horizontal()
        left_layout:add(awful.titlebar.widget.iconwidget(c))
        left_layout:buttons(buttons)

        -- Widgets that are aligned to the right
        local right_layout = wibox.layout.fixed.horizontal()
        right_layout:add(awful.titlebar.widget.floatingbutton(c))
        right_layout:add(awful.titlebar.widget.maximizedbutton(c))
        right_layout:add(awful.titlebar.widget.stickybutton(c))
        right_layout:add(awful.titlebar.widget.ontopbutton(c))
        right_layout:add(awful.titlebar.widget.closebutton(c))

        -- The title goes in the middle
        local middle_layout = wibox.layout.flex.horizontal()
        local title = awful.titlebar.widget.titlewidget(c)
        title:set_align("center")
        middle_layout:add(title)
        middle_layout:buttons(buttons)

        -- Now bring it all together
        local layout = wibox.layout.align.horizontal()
        layout:set_left(left_layout)
        layout:set_right(right_layout)
        layout:set_middle(middle_layout)

        awful.titlebar(c):set_widget(layout)
    end
end)

client.connect_signal("focus", function(c) c.border_color = beautiful.border_focus end)
client.connect_signal("unfocus", function(c) c.border_color = beautiful.border_normal end)
-- }}}
```

---

### Post by fabsjunge on 2014-02-19
Note the line in the global rules rules: [COLOR=#000000][FONT=Ubuntu Mono]keys = clientkeys

[/FONT][/COLOR][FONT=Ubuntu Mono]If clientkeys has not been defined at that point the keybindings will not be bound.
[/FONT][COLOR=#000000][FONT=Ubuntu Mono][/FONT][/COLOR]

---


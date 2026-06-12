---
title: "awesome window placement"
date: 2009-03-07
forum: Desktop Environments
---

### Post by dbbolton on 2009-03-07
I am having trouble with certain windows showing up beyond the edge of the screen in awesome. Here is a screenshot of the open file dialogue from gedit (this also happens with firefox and others):

[[img]http://xs537.xs.to/xs537/09106/2009-03-07-151700_1024x768_scrot462.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs537&d=09106&f=2009-03-07-151700_1024x768_scrot462.png)

Here is how I want it to look (I manually dragged the window back onto the screen) :
[[img]http://xs537.xs.to/xs537/09106/2009-03-07-151713_1024x768_scrot673.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs537&d=09106&f=2009-03-07-151713_1024x768_scrot673.png)

I tried adding this section to my rc.lua file (note the last line):
```

-- Hook function to execute when a new client appears.
awful.hooks.manage.register(function (c, startup)
    -- If we are not managing this application at startup,
    -- move it to the screen where the mouse is.
    -- We only do it for filtered windows (i.e. no dock, etc).
    if not startup and awful.client.focus.filter(c) then
        c.screen = mouse.screen
    end

    if use_titlebar then
        -- Add a titlebar
        awful.titlebar.add(c, { modkey = modkey })
    end
    -- Add mouse bindings
    c:buttons({
        button({ }, 1, function (c) client.focus = c; c:raise() end),
        button({ modkey }, 1, awful.mouse.client.move),
        button({ modkey }, 3, awful.mouse.client.resize)
    })
    -- New client may not receive focus
    -- if they're not focusable, so set border anyway.
    c.border_width = beautiful.border_width
    c.border_color = beautiful.border_normal

    -- Check if the application should be floating.
    local cls = c.class
    local inst = c.instance
    if floatapps[cls] then
        awful.client.floating.set(c, floatapps[cls])
    elseif floatapps[inst] then
        awful.client.floating.set(c, floatapps[inst])
    end

    -- Check application->screen/tag mappings.
    local target
    if apptags[cls] then
        target = apptags[cls]
    elseif apptags[inst] then
        target = apptags[inst]
    end
    if target then
        c.screen = target.screen
        awful.client.movetotag(tags[target.screen][target.tag], c)
    end

    -- Do this after tag mapping, so you don't see it on the wrong tag for a split second.
    client.focus = c

    -- Set key bindings
    c:keys(clientkeys)

    -- Set the windows at the slave,
    -- i.e. put it at the end of others instead of setting it master.
    -- awful.client.setslave(c)

    -- Honor size hints: if you want to drop the gaps between windows, set this to false.
    -- c.size_hints_honor = false
    
    --keep windows from going offscreen
    awful.placement.no_offscreen(c)
end)

```

But that didn't work. Any suggestions?

---


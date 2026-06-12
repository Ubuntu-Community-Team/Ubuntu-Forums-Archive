---
title: "Gnome extension : bug + catch notification app's name"
date: 2018-11-26
forum: Desktop Environments
---

### Post by fthx on 2018-11-26
Hi,

I forked an existing extension to write this one :
[https://extensions.gnome.org/extension/1505/new-mail-indicator/](https://extensions.gnome.org/extension/1505/new-mail-indicator/)

It does work, that's a good point... But :
1) I get some "distribute_natural_allocation: assertion 'extra_space >= 0' failed" in  logs and I don't know why ;
2) I don't know how to catch the app's name that create a notification (here I check if the notif contains a keyword "message", that's a bad hack).

Any help ? Thanks !

Here is extension.js :

```
// you have to modify the message const content to match your language (check it in a Thunderbird or Evolution notification)
// ----------------------------
const message = "message"
// ----------------------------

const St = imports.gi.St;
const Clutter = imports.gi.Clutter;
const Main = imports.ui.main;
const Lang = imports.lang;
const MessagesIndicator = imports.ui.dateMenu.MessagesIndicator;
const IndicatorPad = imports.ui.dateMenu.IndicatorPad;

var label = "0";

const MessageCounterIndicator = new Lang.Class({
    /*
     * See also ui.dateMenu.MessagesIndicator
     */
    Name: 'MessageCounterIndicator',

    _init: function() {
        
        this.actor = new St.BoxLayout({style_class: 'count-label', visible: true});
        
        icon = new St.Icon({ icon_name: 'mail-read-symbolic',
                                    style_class: 'system-status-icon' });
                                    
        this.actor.add_child(icon);
        
        this._sources = [];

        Main.messageTray.connect('source-added', Lang.bind(this, this._onSourceAdded));
        Main.messageTray.connect('source-removed', Lang.bind(this, this._onSourceRemoved));
        Main.messageTray.connect('queue-changed', Lang.bind(this, this._updateCount));

        let sources = Main.messageTray.getSources();
        sources.forEach(Lang.bind(this, function(source) { this._onSourceAdded(null, source); }));
        
        // uncomment next line to get unread email counter
        //mails = new St.Label({text: label, y_align: Clutter.ActorAlign.CENTER});
        
        // uncomment next line to get unread email counter        
        //this.actor.add_child(mails);
    },

    _onSourceAdded: function(tray, source) {
        source.connect('count-updated', Lang.bind(this, this._updateCount));
        this._sources.push(source);
        this._updateCount();
    },

    _onSourceRemoved: function(tray, source) {
        this._sources.splice(this._sources.indexOf(source), 1);
        this._updateCount();
    },

    _updateCount: function() {
        let count = 0;

        this._sources.forEach(Lang.bind(this,
            function(source) {
                for (let i=0; i < source.notifications.length; i++) {
                    let notification = source.notifications[i];
                    if (notification.title.includes(message)) {
                        count++;
                    }
                }
            }));
            
        let mail_icon;
        
        if (count > 0) {
            mail_icon = 'mail-mark-important-symbolic';
            } else {
            mail_icon = 'mail-read-symbolic';
        };
        
        icon.icon_name = mail_icon;

        // uncomment next line to get unread email counter        
        //label = "" + count;

        // uncomment next line to get unread email counter        
        //mails.text = label;
    }
});

let count_indicator, orig_indicator, dateMenu;

function init() {
}

function enable() {

    dateMenu = Main.panel.statusArea.dateMenu;
    let dateMenuLayout = dateMenu.actor.get_children()[0];
    let actors = dateMenuLayout.get_children();

    orig_indicator = dateMenu._indicator;

    // Remove original indicator
    dateMenuLayout.remove_actor(orig_indicator.actor);
    //orig_indicator.actor.destroy();

    // Remove IndicatorPad padding
    dateMenuLayout.remove_actor(actors[0]);

    // Add new indicator
    count_indicator = new MessageCounterIndicator();
    dateMenu._indicator = count_indicator;
    dateMenuLayout.insert_child_at_index(new IndicatorPad(count_indicator.actor), 0);
    dateMenuLayout.add_actor(count_indicator.actor);

}

function disable() {
    let dateMenuLayout = dateMenu.actor.get_children()[0];
    let actors = dateMenuLayout.get_children();

    dateMenuLayout.remove_actor(count_indicator.actor);

    // Remove IndicatorPad padding
    dateMenuLayout.remove_actor(actors[0]);
    actors[0].destroy();

    // Re-add original indicator
    dateMenu._indicator = orig_indicator;
    dateMenuLayout.insert_child_at_index(new IndicatorPad(orig_indicator.actor), 0);
    dateMenuLayout.add_actor(orig_indicator.actor);
}
```

---


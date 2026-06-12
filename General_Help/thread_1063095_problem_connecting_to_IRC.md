---
title: "problem connecting to IRC"
date: 2009-02-07
forum: General Help
---

### Post by jimi_hendrix on 2009-02-07
ok i am not sure where this should go but if this is the wrong place feel free to move it mods

so i am making an irc bot in perl (this is not a programming question dont get turned off) and my irc client of choice (irssi) is using port 6667 happily with irc.freenode.net

however the bot will not connect...it just says the connection times out

i have tried other irc networks with success, but the only network i use is freenode so its worthless to me without connecting to freenode

here is the source code for the bot if you want to see it

[PHP]#!/usr/bin/perl

###################
# A basic irc bot #
###################

use Bot::BasicBot;

$bot = Bot::BasicBot->new(
        server  => "irc.freenode.net",
        port    => "6667",
        channels=> ["#ubuntu-programming"],
        nick    => "jimibot",
        alt_nicks=> ["jbot"],
        username => "jimibot",
        name     => "jimibot",
        ignore_list => [],
        charset => "utf-8");

$bot->run();

[/PHP]

i am posative this is not a programming problem because others have run the bot on their machines and had it work

---


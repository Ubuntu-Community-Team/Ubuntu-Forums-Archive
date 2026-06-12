---
title: "Mailman/Postfix Problem in Intrepid"
date: 2009-01-25
forum: Desktop Environments
---

### Post by jrolland on 2009-01-25
Hello, all!

I have Ubuntu Intrepid running on a 3.4 Ghz Pentium 4. I have installed Postfix and Mailman according to the instructions on <https://help.ubuntu.com/community/Postfix> and <https://help.ubuntu.com/community/Mailman>. Most of it works fine, except that when I send an email to a list, such as <mailman@lists.mydomain.com>, I get the following email back:

Hi. This is the qmail-send program at yahoo.com.
I'm afraid I wasn't able to deliver your message to the following addresses.
This is a permanent error; I've given up. Sorry it didn't work out.

<mailman@lists.mydomain.com>:
75.17.144.000 does not like recipient.
Remote host said: 550 5.1.1 <mailman@mydomain.com>: Recipient address rejected: User unknown in local recipient table
Giving up on 75.17.144.000.

--- Below this line is a copy of the message.

Return-Path: <jrolland@email.com>
Received: (qmail 18087 invoked from network); 25 Jan 2009 22:52:36 -0000
Received: from unknown (HELO ?129.89.249.158?) (jrolland@129.89.249.158 with plain)
*by smtp110.sbc.mail.re2.yahoo.com with SMTP; 25 Jan 2009 22:52:36 -0000
X-YMail-OSG: NT0s8NgVM1meuwDDvOR2OLuVIv0wem5_FcAk9DoT_G2DXVvLVD 2G8i9tSXNshQ9PEgsTMQIxN2FEjgdDxXxuljiQf_8f00xutg_i bkdLspQWPJVBKCD6phb8DPtSURR47iHYI3FLyccIfe_B77RnNb tNX6fgN.6tjjneZdGQnSZFlCIleEQF9hE6UuJUr2wF57Sn8Bng RATLsonZ81w-
X-Yahoo-Newman-Property: ymail-3
Message-Id: <8124B3E7-076D-45FF-9F23-06E57E099013@email.com>
From: Jeffrey Rolland <jrolland@email.com>
To: [email]mailman@lists.mydomain.com[/email]
Content-Type: text/plain; charset=US-ASCII; format=flowed; delsp=yes
Content-Transfer-Encoding: 7bit
Mime-Version: 1.0 (Apple Message framework v930.3)
Subject: Test 7
Date: Sun, 25 Jan 2009 16:52:35 -0600
X-Mailer: Apple Mail (2.930.3)

Test 7
--
Jeffrey Rolland
<jrolland@email.com>

I know the problem has something to do with virtual domains and aliases, but I just don't know what exactly it has to do with them.

Here is the contents of my /etc/postfix/main.cf

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific: Specifying a file name will cause the first
# line of that file to be used as the name. The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

## Gmail Relay
#relayhost = [smtp.gmail.com]:587

## Proxy Relay
proxy_interfaces = 75.17.144.000

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = myserver.mydomain.com
mydomain = mydomain.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = localhost, localhost.localdomain, myserver, mydomain.com, myserver.mydomain.com, mail.mydomain.com, smtp.mydomain.com, lists.mydomain.com, 75.17.144.000
relayhost =
relay_domains = $mydestination
mynetworks = 127.0.0.0/8 192.168.1.0/24
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
home_mailbox = Maildir/
mailbox_command =
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject _unauth_destination
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
transport_maps = hash:/etc/postfix/transport
mailman_destination_recipient_limit = 1
#recipient_delimiter = +
#virtual_alias_domains = mydomain.com
#virtual_alias_maps = hash:/etc/mailman/virtual-mailman

Here is my /etc/postfix/master.cf

#
# Postfix master process configuration file. For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# Do not forget to execute "postfix reload" after editing this file.
#
# ================================================== ========================
# service type private unpriv chroot wakeup maxproc command + args
# (yes) (yes) (yes) (never) (100)
# ================================================== ========================
smtp inet n - - - - smtpd
587 inet n - n - - smtpd
#submission inet n - - - - smtpd
# -o smtpd_tls_security_level=encrypt
# -o smtpd_sasl_auth_enable=yes
# -o smtpd_client_restrictions=permit_sasl_authenticate d,reject
# -o milter_macro_daemon_name=ORIGINATING
#smtps inet n - - - - smtpd
# -o smtpd_tls_wrappermode=yes
# -o smtpd_sasl_auth_enable=yes
# -o smtpd_client_restrictions=permit_sasl_authenticate d,reject
# -o milter_macro_daemon_name=ORIGINATING
#628 inet n - - - - qmqpd
pickup fifo n - - 60 1 pickup
cleanup unix n - - - 0 cleanup
qmgr fifo n - n 300 1 qmgr
#qmgr fifo n - - 300 1 oqmgr
tlsmgr unix - - - 1000? 1 tlsmgr
rewrite unix - - - - - trivial-rewrite
bounce unix - - - - 0 bounce
defer unix - - - - 0 bounce
trace unix - - - - 0 bounce
verify unix - - - - 1 verify
flush unix n - - 1000? 0 flush
proxymap unix - - n - - proxymap
proxywrite unix - - n - 1 proxymap
smtp unix - - - - - smtp
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay unix - - - - - smtp
-o smtp_fallback_relay=
-o smtp_generic_maps=
# -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq unix n - - - - showq
error unix - - - - - error
retry unix - - - - - error
discard unix - - - - - discard
local unix - n n - - local
virtual unix - n n - - virtual
lmtp unix - - - - - lmtp
anvil unix - - - - 1 anvil
scache unix - - - - 1 scache
#
# ================================================== ==================
# Interfaces to non-Postfix software. Be sure to examine the manual
# pages of the non-Postfix software to find out what options it wants.
#
# Many of the following services use the Postfix pipe( delivery
# agent. See the pipe( man page for information about ${recipient}
# and other message envelope options.
# ================================================== ==================
#
# maildrop. See the Postfix MAILDROP_README file for details.
# Also specify in main.cf: maildrop_destination_recipient_limit=1
#
maildrop unix - n n - - pipe
flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
#
# See the Postfix UUCP_README file for configuration details.
#
uucp unix - n n - - pipe
flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
#
# Other external delivery methods.
#
ifmail unix - n n - - pipe
flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp unix - n n - - pipe
flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix - n n - 2 pipe
flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman unix - n n - - pipe
flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
${nexthop} ${user}

Here is my /etc/postfix/transport

lists.mydomain.com mailman:

Here is my /etc/mailman/mm_cfg.py

# -*- python -*-

# Copyright (C) 1998,1999,2000 by the Free Software Foundation, Inc.
#
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# as published by the Free Software Foundation; either version 2
# of the License, or (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA
# 02110-1301 USA


"""This is the module which takes your site-specific settings.

From a raw distribution it should be copied to mm_cfg.py. If you
already have an mm_cfg.py, be careful to add in only the new settings
you want. The complete set of distributed defaults, with annotation,
are in ./Defaults. In mm_cfg, override only those you want to
change, after the

from Defaults import *

line (see below).

Note that these are just default settings - many can be overridden via the
admin and user interfaces on a per-list or per-user basis.

Note also that some of the settings are resolved against the active list
setting by using the value as a format string against the
list-instance-object's dictionary - see the distributed value of
DEFAULT_MSG_FOOTER for an example."""


################################################## #####
# Here's where we get the distributed defaults. #

from Defaults import *

################################################## ############
# Put YOUR site-specific configuration below, in mm_cfg.py . #
# See Defaults.py for explanations of the values. #

#-------------------------------------------------------------
# The name of the list Mailman uses to send password reminders
# and similar. Don't change if you want mailman-owner to be
# a valid local part.
MAILMAN_SITE_LIST = 'mailman'

#-------------------------------------------------------------
# If you change these, you have to configure your http server
# accordingly (Alias and ScriptAlias directives in most httpds)
DEFAULT_URL_PATTERN = 'http://%s/cgi-bin/mailman/'
PRIVATE_ARCHIVE_URL = '/cgi-bin/mailman/private'
IMAGE_LOGOS = '/images/mailman/'

#-------------------------------------------------------------
# Default domain for email addresses of newly created MLs
DEFAULT_EMAIL_HOST = 'mydomain.com'
#-------------------------------------------------------------
# Default host for web interface of newly created MLs
DEFAULT_URL_HOST = 'www.mydomain.com'
#-------------------------------------------------------------
# Required when setting any of its arguments.
add_virtualhost(DEFAULT_URL_HOST, DEFAULT_EMAIL_HOST)

#-------------------------------------------------------------
# The default language for this server.
DEFAULT_SERVER_LANGUAGE = 'en'

#-------------------------------------------------------------
# Iirc this was used in pre 2.1, leave it for now
USE_ENVELOPE_SENDER = 0 # Still used?

#-------------------------------------------------------------
# Unset send_reminders on newly created lists
DEFAULT_SEND_REMINDERS = 0

#-------------------------------------------------------------
# Uncomment this if you configured your MTA such that it
# automatically recognizes newly created lists.
# (see /usr/share/doc/mailman/README.Exim4.Debian)
# MTA=None # Misnomer, suppresses alias output on newlist

#-------------------------------------------------------------
# Uncomment if you use Postfix virtual domains, but be sure to
# see /usr/share/doc/mailman/README.Debian first.
# MTA='Postfix'

# POSTFIX_STYLE_VIRTUAL_DOMAINS = []

#-------------------------------------------------------------
# Uncomment if you want to filter mail with SpamAssassin. For
# more information please visit this website:
# [http://www.jamesh.id.au/articles/mailman-spamassassin/](http://www.jamesh.id.au/articles/mailman-spamassassin/)
# GLOBAL_PIPELINE.insert(1, 'SpamAssassin')

# Note - if you're looking for something that is imported from mm_cfg, but you
# didn't find it above, it's probably in /usr/lib/mailman/Mailman/Defaults.py.

Any assistance you can provide is appreciated

Sincerely,
Jeffrey Rolland

---


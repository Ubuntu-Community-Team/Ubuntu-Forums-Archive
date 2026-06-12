---
title: "(liferea-bin:8376): Gtk-WARNING **: GtkSpinButton: non-zer"
date: 2009-02-06
forum: General Help
---

### Post by Xamiga on 2009-02-06
Just started this morning:
Liferea dies.

(liferea-bin:8376): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
Segmentation fault

complete removal and reinstall didn't help.

how to fix?

```

TRACE: + rule_init
TRACE: - rule_init
TRACE: + db_init
DB: Opening DB file /home/al/.liferea_1.4/liferea.db...
DB: current DB schema version: 7
DB: executing SQL: CREATE TABLE items (   title		TEXT,   read		INTEGER,   new		INTEGER,   updated		INTEGER,   popup		INTEGER,   marked		INTEGER,   source		TEXT,   source_id		TEXT,   valid_guid		INTEGER,   real_source_url	TEXT,   real_source_title	TEXT,   description	TEXT,   date		INTEGER,   comment_feed_id	TEXT,   comment            INTEGER);
DB:  -> result: 1 (table items already exists)
DB: executing SQL: CREATE INDEX items_idx ON items (source_id);
DB:  -> result: 1 (index items_idx already exists)
DB: executing SQL: CREATE INDEX items_idx2 ON items (comment_feed_id);
DB:  -> result: 1 (index items_idx2 already exists)
DB: executing SQL: CREATE TABLE itemsets (   item_id		INTEGER,   parent_item_id     INTEGER,   node_id	TEXT,   parent_node_id     TEXT,   read		INTEGER,   comment            INTEGER,   PRIMARY KEY (item_id, node_id));
DB:  -> result: 1 (table itemsets already exists)
DB: executing SQL: CREATE INDEX itemset_idx  ON itemsets (node_id);
DB:  -> result: 1 (index itemset_idx already exists)
DB: executing SQL: CREATE INDEX itemset_idx2 ON itemsets (item_id);
DB:  -> result: 1 (index itemset_idx2 already exists)
DB: executing SQL: CREATE TABLE metadata (   item_id		INTEGER,   nr              	INTEGER,   key             	TEXT,   value           	TEXT,   PRIMARY KEY (item_id, nr));
DB:  -> result: 1 (table metadata already exists)
DB: executing SQL: CREATE INDEX metadata_idx ON metadata (item_id);
DB:  -> result: 1 (index metadata_idx already exists)
DB: executing SQL: CREATE TABLE subscription (   node_id            STRING,   source             STRING,   orig_source        STRING,   filter_cmd         STRING,   update_interval	INTEGER,   default_interval   INTEGER,   discontinued       INTEGER,   available          INTEGER,   PRIMARY KEY (node_id));
DB:  -> result: 1 (table subscription already exists)
DB: executing SQL: CREATE TABLE update_state (   node_id            STRING,   last_modified      STRING,   etag               STRING,   last_update        INTEGER,   last_favicon_update INTEGER,   PRIMARY KEY (node_id));
DB:  -> result: 1 (table update_state already exists)
DB: executing SQL: CREATE TABLE subscription_metadata (   node_id            STRING,   nr                 INTEGER,   key                TEXT,   value              TEXT,   PRIMARY KEY (node_id, nr));
DB:  -> result: 1 (table subscription_metadata already exists)
DB: executing SQL: CREATE INDEX subscription_metadata_idx ON subscription_metadata (node_id);
DB:  -> result: 1 (index subscription_metadata_idx already exists)
DB: executing SQL: CREATE TABLE node (   node_id		STRING,   parent_id		STRING,   title		STRING,   type		INTEGER,   expanded           INTEGER,   view_mode		INTEGER,   sort_column	INTEGER,   sort_reversed	INTEGER,   PRIMARY KEY (node_id));
DB:  -> result: 1 (table node already exists)
DB: executing SQL: CREATE TABLE view_state (   node_id            STRING,   unread             INTEGER,   count              INTEGER,   PRIMARY KEY (node_id));
DB:  -> result: 1 (table view_state already exists)
DB: executing SQL: DROP TRIGGER item_insert;
DB:  -> result: 0 (success)
DB: executing SQL: DROP TRIGGER item_update;
DB:  -> result: 0 (success)
DB: executing SQL: DROP TRIGGER item_removal;
DB:  -> result: 0 (success)
DB: executing SQL: DROP TRIGGER subscription_removal;
DB:  -> result: 0 (success)
DB: Checking for items not referenced in table 'itemsets'...

DB: executing SQL: BEGIN;    CREATE TEMP TABLE tmp_id ( id );   INSERT INTO tmp_id SELECT ROWID FROM items WHERE ROWID NOT IN (SELECT item_id FROM itemsets);   DELETE FROM items WHERE ROWID IN (SELECT id FROM tmp_id LIMIT 1000);   DROP TABLE tmp_id;END;
DB:  -> result: 0 (success)
DB: Checking for invalid item ids in table 'itemsets'...

DB: executing SQL: BEGIN;    CREATE TEMP TABLE tmp_id ( id );   INSERT INTO tmp_id SELECT item_id FROM itemsets WHERE item_id NOT IN (SELECT ROWID FROM items);   DELETE FROM itemsets WHERE item_id IN (SELECT id FROM tmp_id LIMIT 1000);   DROP TABLE tmp_id;END;
DB:  -> result: 0 (success)
DB: Checking for items without a subscription...

DB: executing SQL: DELETE FROM itemsets WHERE comment = 0 AND node_id NOT IN (SELECT node_id FROM subscription);
DB:  -> result: 0 (success)
DB: DB cleanup finished. Continuing startup.

DB: executing SQL: CREATE TRIGGER item_insert INSERT ON items BEGIN    UPDATE itemsets SET read = new.read    WHERE item_id = new.ROWID; END;
DB:  -> result: 0 (success)
DB: executing SQL: CREATE TRIGGER item_update UPDATE ON items BEGIN    UPDATE itemsets SET read = new.read    WHERE item_id = new.ROWID; END;
DB:  -> result: 0 (success)
DB: executing SQL: CREATE TRIGGER item_removal DELETE ON itemsets BEGIN    DELETE FROM items WHERE ROWID = old.item_id;    DELETE FROM metadata WHERE item_id = old.item_id; END;
DB:  -> result: 0 (success)
DB: executing SQL: CREATE TRIGGER subscription_removal DELETE ON subscription BEGIN    DELETE FROM node WHERE node_id = old.node_id;    DELETE FROM update_state WHERE node_id = old.node_id;    DELETE FROM subscription_metadata WHERE node_id = old.node_id; END;
DB:  -> result: 0 (success)
TRACE: - db_init
CONF: proxy is disabled by user
CONF: Proxy settings are now NULL:0 NULL:NULL
TRACE: + plugin_mgmt_get_init
PLUGINS: Scanning for plugins (/usr/lib/liferea):
PLUGINS: -> XulRunner Rendering Plugin (liblihtmlx.so, type=0)
PLUGINS: -> LUA Scripting Support Plugin (libliscrlua.so, type=4)
PLUGINS: -> libnotify notification (liblinotiflibnotify.so, type=3)
PLUGINS: using "XulRunner" for HTML rendering...
TRACE: + mozembed_init (XPCOM_GLUE)
TRACE: - mozembed_init
PLUGINS: using "libnotify" for notification type 0
TRACE: - plugin_mgmt_init
PLUGINS: using "LUA Scripting Support Plugin" for scripting...
TRACE: + ui_mainwindow_init

(liferea-bin:8502): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
TRACE: + ui_feedlist_init
TRACE: - ui_feedlist_init
TRACE: + feedlist_init
CACHE: Setting up root node
TRACE: + node_source_setup_root
TRACE: + default_source_source_import
CACHE: Importing OPML file: /home/al/.liferea_1.4/feedlist.opml
TRACE: + import_parse_outline
CACHE: -> node type tag found: "folder"
GUI: adding node "International" as child of parent="root"
GUI: folder empty check for node id "jhukbfk"
GUI: folder empty check for node id "hpmkuol"
TRACE: + import_parse_outline
CACHE: -> node type tag found: "folder"
GUI: adding node "Open Source" as child of parent="International"
GUI: folder empty check for node id "hpmkuol"
GUI: folder empty check for node id "qklgtfu"
TRACE: + import_parse_outline
CACHE: -> node type tag found: "rss"
DB: loading subscription xtudtcm update state (thread=0x9e25f78)
TRACE: + favicon_load_from_cache
TRACE: - favicon_load_from_cache
CACHE: import feed: title=Gnomefiles source=http://www.gnomefiles.org/files/gnomefiles.rdf typeStr= interval=-1
GUI: adding node "Gnomefiles" as child of parent="Open Source"
GUI: folder empty check for node id "qklgtfu"
DB: updating node info xtudtcm (thread 0x9e25f78)
TRACE: - import_parse_outline
TRACE: + import_parse_outline
CACHE: -> node type tag found: "rss"
DB: loading subscription dvwpgiy update state (thread=0x9e25f78)
DB: update state load took 0,003s
TRACE: + favicon_load_from_cache
TRACE: - favicon_load_from_cache
CACHE: import feed: title=GNOME Footnotes source=http://www.gnomedesktop.org/backend.php typeStr= interval=-1
GUI: adding node "GNOME Footnotes" as child of parent="Open Source"
GUI: folder empty check for node id "qklgtfu"
DB: updating node info dvwpgiy (thread 0x9e25f78)
TRACE: - import_parse_outline
TRACE: + import_parse_outline
CACHE: -> node type tag found: "rss"
DB: loading subscription jqrdtib update state (thread=0x9e25f78)
DB: update state load took 0,003s
TRACE: + favicon_load_from_cache
TRACE: - favicon_load_from_cache
CACHE: import feed: title=mozillaZine source=http://www.mozillazine.org/contents.rdf typeStr= interval=-1
GUI: adding node "mozillaZine" as child of parent="Open Source"
GUI: folder empty check for node id "qklgtfu"
DB: updating node info jqrdtib (thread 0x9e25f78)
TRACE: - import_parse_outline
TRACE: + import_parse_outline
CACHE: -> node type tag found: "pie"
DB: loading subscription jkxubay update state (thread=0x9e25f78)
DB: update state load took 0,003s
TRACE: + favicon_load_from_cache
TRACE: - favicon_load_from_cache
CACHE: import feed: title=Planet GNOME source=http://planet.gnome.org/atom.xml typeStr= interval=-1
GUI: adding node "Planet GNOME" as child of parent="Open Source"
GUI: folder empty check for node id "qklgtfu"
DB: updating node info jkxubay (thread 0x9e25f78)
TRACE: - import_parse_outline
TRACE: + import_parse_outline
CACHE: -> node type tag found: "rss"
DB: loading subscription rlppnfe update state (thread=0x9e25f78)
DB: update state load took 0,003s
TRACE: + favicon_load_from_cache
TRACE: - favicon_load_from_cache
CACHE: import feed: title=Slashdot source=http://slashdot.org/slashdot.rss typeStr= interval=60
GUI: adding node "Slashdot" as child of parent="Open Source"
GUI: folder empty check for node id "qklgtfu"
DB: updating node info rlppnfe (thread 0x9e25f78)
TRACE: - import_parse_outline
TRACE: + import_parse_outline
CACHE: -> node type tag found: "rss"
DB: loading subscription xbufcvi update state (thread=0x9e25f78)
DB: update state load took 0,003s
TRACE: + favicon_load_from_cache
TRACE: - favicon_load_from_cache
CACHE: import feed: title=Earthquakes source=http://earthquake.usgs.gov/eqcenter/catalogs/eqs7day-M5.xml typeStr= interval=-1
GUI: adding node "Earthquakes" as child of parent="Open Source"
GUI: folder empty check for node id "qklgtfu"
DB: updating node info xbufcvi (thread 0x9e25f78)
TRACE: - import_parse_outline
TRACE: + import_parse_outline
CACHE: -> node type tag found: "rss"
DB: loading subscription poaekoy update state (thread=0x9e25f78)
DB: update state load took 0,003s
TRACE: + favicon_load_from_cache
TRACE: - favicon_load_from_cache
CACHE: import feed: title=Powell River source=http://www.prpeak.com/?rss=news typeStr= interval=4320
GUI: adding node "Powell River" as child of parent="Open Source"
GUI: folder empty check for node id "qklgtfu"
DB: updating node info poaekoy (thread 0x9e25f78)
TRACE: - import_parse_outline
TRACE: + import_parse_outline
CACHE: -> node type tag found: "rss"
DB: loading subscription qfhhemx update state (thread=0x9e25f78)
DB: update state load took 0,003s
TRACE: + favicon_load_from_cache
TRACE: - favicon_load_from_cache
CACHE: import feed: title=Ubuntu Forums source=http://ubuntuforums.org/external.php?type=RSS2 typeStr= interval=60
GUI: adding node "Ubuntu Forums" as child of parent="Open Source"
GUI: folder empty check for node id "qklgtfu"
DB: updating node info qfhhemx (thread 0x9e25f78)
TRACE: - import_parse_outline
TRACE: + import_parse_outline
CACHE: -> node type tag found: "rss"
DB: loading subscription japqlwe update state (thread=0x9e25f78)
DB: update state load took 0,003s
TRACE: + favicon_load_from_cache
TRACE: - favicon_load_from_cache
CACHE: import feed: title=ATI Drivers source=http://www.ati.com/online/rss/atilinuxdriver.rss typeStr= interval=14400
GUI: adding node "ATI Drivers" as child of parent="Open Source"
GUI: folder empty check for node id "qklgtfu"
DB: updating node info japqlwe (thread 0x9e25f78)
TRACE: - import_parse_outline
TRACE: + import_parse_outline
CACHE: -> node type tag found: "rss"
DB: loading subscription swygvou update state (thread=0x9e25f78)
DB: update state load took 0,003s
TRACE: + favicon_load_from_cache
TRACE: - favicon_load_from_cache
CACHE: import feed: title=All about Linux source=http://feeds2.feedburner.com/AllAboutLinux typeStr= interval=10080
GUI: adding node "All about Linux" as child of parent="Open Source"
GUI: folder empty check for node id "qklgtfu"
DB: updating node info swygvou (thread 0x9e25f78)
TRACE: - import_parse_outline
DB: updating node info qklgtfu (thread 0x9e25f78)
TRACE: - import_parse_outline
DB: updating node info hpmkuol (thread 0x9e25f78)
TRACE: - import_parse_outline
TRACE: + import_parse_outline
CACHE: -> node type tag found: "vfolder"
CACHE: import vfolder: title=Unread
TRACE: + vfolder_new
TRACE: - vfolder_new
CACHE: loading rule "unread" ""
GUI: adding node "Unread" as child of parent="root"
GUI: folder empty check for node id "jhukbfk"
DB: Checking for view xqqssyg (SQL=CREATE VIEW view_xqqssyg AS SELECT items.ROWID AS item_id,items.read AS item_read FROM items   WHERE (items.read = 0) AND items.comment != 1)
DB: No need to create view xqqssyg as it already exists.
DB: executing SQL: REPLACE INTO view_state (node_id, unread, count) VALUES ('xqqssyg',    (SELECT count(*) FROM view_xqqssyg WHERE item_read = 0),   (SELECT count(*) FROM view_xqqssyg));
DB:  -> result: 0 (success)
DB: updating node info xqqssyg (thread 0x9e25f78)
DB: subscription_update took 0,003s
TRACE: - import_parse_outline
DB: checking for lost subscriptions...
TRACE: - default_source_source_import
TRACE: - node_source_setup_root
CACHE: Initializing node state
PARSING: unknown metadata type (description)
CACHE: Unknown metadata type "description", this is a program bug! Treating as HTML.
PARSING: unknown metadata type (description)
CACHE: Unknown metadata type "description", this is a program bug! Treating as HTML.
PARSING: unknown metadata type (description)
CACHE: Unknown metadata type "description", this is a program bug! Treating as HTML.
PARSING: unknown metadata type (description)
CACHE: Unknown metadata type "description", this is a program bug! Treating as HTML.
PARSING: unknown metadata type (description)
CACHE: Unknown metadata type "description", this is a program bug! Treating as HTML.
PARSING: unknown metadata type (description)
CACHE: Unknown metadata type "description", this is a program bug! Treating as HTML.
PARSING: unknown metadata type (description)
CACHE: Unknown metadata type "description", this is a program bug! Treating as HTML.
PARSING: unknown metadata type (description)
CACHE: Unknown metadata type "description", this is a program bug! Treating as HTML.
PARSING: unknown metadata type (description)
CACHE: Unknown metadata type "description", this is a program bug! Treating as HTML.
GUI: Notification setup
UPDATE: Performing initial feed update
UPDATE: initial update: updating all feeds
UPDATE: Scheduling Gnomefiles to be updated
DB: saving subscription xtudtcm update state (thread=0x9e25f78)
UPDATE: Resetting last poll counter to 1233969548.
UPDATE: processing request (http://www.gnomefiles.org/files/gnomefiles.rdf)
UPDATE: downloading http://www.gnomefiles.org/files/gnomefiles.rdf
NET: downloading url=/files/gnomefiles.rdf host=www.gnomefiles.org
NET: NetConnect() (with getaddrinfo)
NET: host=www.gnomefiles.org port=80
Segmentation fault

```

---


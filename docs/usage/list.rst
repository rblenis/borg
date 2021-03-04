.. include:: list.rst.inc

Examples
~~~~~~~~
::

    $ borg list /path/to/repo
    Monday                               Mon, 2016-02-15 19:15:11
    repo                                 Mon, 2016-02-15 19:26:54
    root-2016-02-15                      Mon, 2016-02-15 19:36:29
    newname                              Mon, 2016-02-15 19:50:19
    ...

    $ borg list /path/to/repo::root-2016-02-15
    drwxr-xr-x root   root          0 Mon, 2016-02-15 17:44:27 .
    drwxrwxr-x root   root          0 Mon, 2016-02-15 19:04:49 bin
    -rwxr-xr-x root   root    1029624 Thu, 2014-11-13 00:08:51 bin/bash
    lrwxrwxrwx root   root          0 Fri, 2015-03-27 20:24:26 bin/bzcmp -> bzdiff
    -rwxr-xr-x root   root       2140 Fri, 2015-03-27 20:24:22 bin/bzdiff
    ...

    $ borg list /path/to/repo::root-2016-02-15 --pattern "- bin/ba*"
    drwxr-xr-x root   root          0 Mon, 2016-02-15 17:44:27 .
    drwxrwxr-x root   root          0 Mon, 2016-02-15 19:04:49 bin
    lrwxrwxrwx root   root          0 Fri, 2015-03-27 20:24:26 bin/bzcmp -> bzdiff
    -rwxr-xr-x root   root       2140 Fri, 2015-03-27 20:24:22 bin/bzdiff
    ...

    $ borg list /path/to/repo::archiveA --format="{mode} {user:6} {group:6} {size:8d} {isomtime} {path}{extra}{NEWLINE}"
    drwxrwxr-x user   user          0 Sun, 2015-02-01 11:00:00 .
    drwxrwxr-x user   user          0 Sun, 2015-02-01 11:00:00 code
    drwxrwxr-x user   user          0 Sun, 2015-02-01 11:00:00 code/myproject
    -rw-rw-r-- user   user    1416192 Sun, 2015-02-01 11:00:00 code/myproject/file.ext
    ...

    $ borg list /path/to/repo::root-2016-02-15 --json-lines
    {"type": "d", "mode": "drwxr-xr-x", "user": "root", "group": "root", "uid": 0, "gid": 0, "path": ".", 'size": 0, "mtime": "2016-02-15T17:44:27.0"}
    {"type": "d", "mode": "drwxr-xr-x", "user": "root", "group": "root", "uid": 0, "gid": 0, "path": "bin", "size": 0, "mtime": "2016-02-15T19:04:49.0"}
    {"type": "-", "mode": "-rwxr-xr-x", "user": "root", "group": "root", "uid": 0, "gid": 0, "path": "bin/bash", "size": 1029624, "mtime": "2014-11-13T00:08:51.0"}
    {"type": "l", "mode": "lrwxrwxrwx", "user": "root", "group": "root", "uid": 0, "gid": 0, "path": "bin/bacmp", "size": 0, "mtime": "2015-03-27T20:24:26.0", "linktarget": "bzdiff"}
    {"type": "-", "mode": "-rwxr-xr-x", "user": "root", "group": "root", "uid": 0, "gid": 0, "path": "bin/bzdiff", "size": 2140, "mtime": "2015-03-27T20:24:22.0"}
    ...

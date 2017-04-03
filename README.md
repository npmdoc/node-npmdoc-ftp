# api documentation for  [ftp (v0.3.10)](https://github.com/mscdex/node-ftp)  [![npm package](https://img.shields.io/npm/v/npmdoc-ftp.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-ftp) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-ftp.svg)](https://travis-ci.org/npmdoc/node-npmdoc-ftp)
#### An FTP client module for node.js

[![NPM](https://nodei.co/npm/ftp.png?downloads=true)](https://www.npmjs.com/package/ftp)

[![apidoc](https://npmdoc.github.io/node-npmdoc-ftp/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-ftp_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-ftp/build..beta..travis-ci.org/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-ftp/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-ftp/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Brian White",
        "email": "mscdex@mscdex.net"
    },
    "bugs": {
        "url": "https://github.com/mscdex/node-ftp/issues"
    },
    "dependencies": {
        "readable-stream": "1.1.x",
        "xregexp": "2.0.0"
    },
    "description": "An FTP client module for node.js",
    "devDependencies": {},
    "directories": {},
    "dist": {
        "shasum": "9197d861ad8142f3e63d5a83bfe4c59f7330885d",
        "tarball": "https://registry.npmjs.org/ftp/-/ftp-0.3.10.tgz"
    },
    "engines": {
        "node": ">=0.8.0"
    },
    "homepage": "https://github.com/mscdex/node-ftp",
    "keywords": [
        "ftp",
        "client",
        "transfer"
    ],
    "licenses": [
        {
            "type": "MIT",
            "url": "http://github.com/mscdex/node-ftp/raw/master/LICENSE"
        }
    ],
    "main": "./lib/connection",
    "maintainers": [
        {
            "name": "mscdex",
            "email": "mscdex@mscdex.net"
        }
    ],
    "name": "ftp",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git+ssh://git@github.com/mscdex/node-ftp.git"
    },
    "scripts": {
        "test": "node test/test.js"
    },
    "version": "0.3.10"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module ftp](#apidoc.module.ftp)
1.  [function <span class="apidocSignatureSpan">ftp.</span>parser (options)](#apidoc.element.ftp.parser)
1.  [function <span class="apidocSignatureSpan">ftp.</span>super_ ()](#apidoc.element.ftp.super_)
1.  object <span class="apidocSignatureSpan">ftp.</span>parser.prototype

#### [module ftp.parser](#apidoc.module.ftp.parser)
1.  [function <span class="apidocSignatureSpan">ftp.</span>parser (options)](#apidoc.element.ftp.parser.parser)
1.  [function <span class="apidocSignatureSpan">ftp.parser.</span>parseFeat (text)](#apidoc.element.ftp.parser.parseFeat)
1.  [function <span class="apidocSignatureSpan">ftp.parser.</span>parseListEntry (line)](#apidoc.element.ftp.parser.parseListEntry)
1.  [function <span class="apidocSignatureSpan">ftp.parser.</span>super_ (options)](#apidoc.element.ftp.parser.super_)

#### [module ftp.parser.prototype](#apidoc.module.ftp.parser.prototype)
1.  [function <span class="apidocSignatureSpan">ftp.parser.prototype.</span>_write (chunk, encoding, cb)](#apidoc.element.ftp.parser.prototype._write)



# <a name="apidoc.module.ftp"></a>[module ftp](#apidoc.module.ftp)

#### <a name="apidoc.element.ftp.parser"></a>[function <span class="apidocSignatureSpan">ftp.</span>parser (options)](#apidoc.element.ftp.parser)
- description and source-code
```javascript
function Parser(options) {
  if (!(this instanceof Parser))
    return new Parser(options);
  WritableStream.call(this);

  this._buffer = '';
  this._debug = options.debug;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.ftp.super_"></a>[function <span class="apidocSignatureSpan">ftp.</span>super_ ()](#apidoc.element.ftp.super_)
- description and source-code
```javascript
function EventEmitter() {
  EventEmitter.init.call(this);
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.ftp.parser"></a>[module ftp.parser](#apidoc.module.ftp.parser)

#### <a name="apidoc.element.ftp.parser.parser"></a>[function <span class="apidocSignatureSpan">ftp.</span>parser (options)](#apidoc.element.ftp.parser.parser)
- description and source-code
```javascript
function Parser(options) {
  if (!(this instanceof Parser))
    return new Parser(options);
  WritableStream.call(this);

  this._buffer = '';
  this._debug = options.debug;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.ftp.parser.parseFeat"></a>[function <span class="apidocSignatureSpan">ftp.parser.</span>parseFeat (text)](#apidoc.element.ftp.parser.parseFeat)
- description and source-code
```javascript
parseFeat = function (text) {
  var lines = text.split(RE_EOL);
  lines.shift(); // initial response line
  lines.pop(); // final response line

  for (var i = 0, len = lines.length; i < len; ++i)
    lines[i] = lines[i].trim();

  // just return the raw lines for now
  return lines;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.ftp.parser.parseListEntry"></a>[function <span class="apidocSignatureSpan">ftp.parser.</span>parseListEntry (line)](#apidoc.element.ftp.parser.parseListEntry)
- description and source-code
```javascript
parseListEntry = function (line) {
  var ret,
      info,
      month, day, year,
      hour, mins;

  if (ret = XRegExp.exec(line, REX_LISTUNIX)) {
    info = {
      type: ret.type,
      name: undefined,
      target: undefined,
      sticky: false,
      rights: {
        user: ret.permission.substr(0, 3).replace(RE_DASH, ''),
        group: ret.permission.substr(3, 3).replace(RE_DASH, ''),
        other: ret.permission.substr(6, 3).replace(RE_DASH, '')
      },
      acl: (ret.acl === '+'),
      owner: ret.owner,
      group: ret.group,
      size: parseInt(ret.size, 10),
      date: undefined
    };

    // check for sticky bit
    var lastbit = info.rights.other.slice(-1);
    if (lastbit === 't') {
      info.rights.other = info.rights.other.slice(0, -1) + 'x';
      info.sticky = true;
    } else if (lastbit === 'T') {
      info.rights.other = info.rights.other.slice(0, -1);
      info.sticky = true;
    }

    if (ret.month1 !== undefined) {
      month = parseInt(MONTHS[ret.month1.toLowerCase()], 10);
      day = parseInt(ret.date1, 10);
      year = (new Date()).getFullYear();
      hour = parseInt(ret.hour, 10);
      mins = parseInt(ret.minute, 10);
      if (month < 10)
        month = '0' + month;
      if (day < 10)
        day = '0' + day;
      if (hour < 10)
        hour = '0' + hour;
      if (mins < 10)
        mins = '0' + mins;
      info.date = new Date(year + '-'
                           + month + '-'
                           + day + 'T'
                           + hour + ':'
                           + mins);
      // If the date is in the past but no more than 6 months old, year
      // isn't displayed and doesn't have to be the current year.
      //
      // If the date is in the future (less than an hour from now), year
      // isn't displayed and doesn't have to be the current year.
      // That second case is much more rare than the first and less annoying.
      // It's impossible to fix without knowing about the server's timezone,
      // so we just don't do anything about it.
      //
      // If we're here with a time that is more than 28 hours into the
      // future (1 hour + maximum timezone offset which is 27 hours),
      // there is a problem -- we should be in the second conditional block
      if (info.date.getTime() - Date.now() > 100800000) {
        info.date = new Date((year - 1) + '-'
                             + month + '-'
                             + day + 'T'
                             + hour + ':'
                             + mins);
      }

      // If we're here with a time that is more than 6 months old, there's
      // a problem as well.
      // Maybe local & remote servers aren't on the same timezone (with remote
      // ahead of local)
      // For instance, remote is in 2014 while local is still in 2013. In
      // this case, a date like 01/01/13 02:23 could be detected instead of
      // 01/01/14 02:23
      // Our trigger point will be 3600*24*31*6 (since we already use 31
      // as an upper bound, no need to add the 27 hours timezone offset)
      if (Date.now() - info.date.getTime() > 16070400000) {
        info.date = new Date((year + 1) + '-'
                             + month + '-'
                             + day + 'T'
                             + hour + ':'
                             + mins);
      }
    } else if (ret.month2 !== undefined) {
      month = parseInt(MONTHS[ret.month2.toLowerCase()], 10);
      day = parseInt(ret.date2, 10);
      year = parseInt(ret.year, 10);
      if (month < 10)
        month = '0' + month;
      if (day < 10)
        day = '0' + day;
      info.date = new Date(year + '-' + month + '-' + day);
    }
    if (ret.type === 'l') {
      var pos = ret.name.indexOf(' -> ');
      info.name = ret.name.substring(0, pos);
      info.target = ret.name.substring(pos+4);
    } else
      info.name = ret.name;
    ret = info;
  } else if (ret = XRegExp.exec(line, REX_LISTMSDOS)) {
    info = {
      name: ret.name,
      type: (ret.isdir ? 'd' : '-'),
      size: (ret.isdir ? 0 : parseInt(ret.size, 10)), ...
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.ftp.parser.super_"></a>[function <span class="apidocSignatureSpan">ftp.parser.</span>super_ (options)](#apidoc.element.ftp.parser.super_)
- description and source-code
```javascript
function Writable(options) {
  // Writable ctor is applied to Duplexes, too.
  // 'realHasInstance' is necessary because using plain 'instanceof'
  // would return false, as no '_writableState' property is attached.

  // Trying to use the custom 'instanceof' for Writable here will also break the
  // Node.js LazyTransform implementation, which has a non-trivial getter for
  // '_writableState' that would lead to infinite recursion.
  if (!(realHasInstance.call(Writable, this)) &&
      !(this instanceof Stream.Duplex)) {
    return new Writable(options);
  }

  this._writableState = new WritableState(options, this);

  // legacy.
  this.writable = true;

  if (options) {
    if (typeof options.write === 'function')
      this._write = options.write;

    if (typeof options.writev === 'function')
      this._writev = options.writev;
  }

  Stream.call(this);
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.ftp.parser.prototype"></a>[module ftp.parser.prototype](#apidoc.module.ftp.parser.prototype)

#### <a name="apidoc.element.ftp.parser.prototype._write"></a>[function <span class="apidocSignatureSpan">ftp.parser.prototype.</span>_write (chunk, encoding, cb)](#apidoc.element.ftp.parser.prototype._write)
- description and source-code
```javascript
_write = function (chunk, encoding, cb) {
  var m, code, reRmLeadCode, rest = '', debug = this._debug;

  this._buffer += chunk.toString('binary');

  while (m = RE_RES_END.exec(this._buffer)) {
    // support multiple terminating responses in the buffer
    rest = this._buffer.substring(m.index + m[0].length);
    if (rest.length)
      this._buffer = this._buffer.substring(0, m.index + m[0].length);

    debug&&debug('[parser] < ' + inspect(this._buffer));

    // we have a terminating response line
    code = parseInt(m[1], 10);

    // RFC 959 does not require each line in a multi-line response to begin
    // with '<code>-', but many servers will do this.
    //
    // remove this leading '<code>-' (or '<code> ' from last line) from each
    // line in the response ...
    reRmLeadCode = '(^|\\r?\\n)';
    reRmLeadCode += m[1];
    reRmLeadCode += '(?: |\\-)';
    reRmLeadCode = new RegExp(reRmLeadCode, 'g');
    var text = this._buffer.replace(reRmLeadCode, '$1').trim();
    this._buffer = rest;

    debug&&debug('[parser] Response: code=' + code + ', buffer=' + inspect(text));
    this.emit('response', code, text);
  }

  cb();
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)

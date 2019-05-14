## Python Proxy Requests | make an http GET/POST with a proxy scraped from https://www.sslproxies.org/
pypi.org: https://pypi.org/project/proxy-requests/
<br><br>
The ProxyRequests class first scrapes proxies from the web. Then it recursively attempts to make a request if the initial request with a proxy is unsuccessful.
<br><br>
Either copy the code and put where you want it, or download via pip:
<br><br>
<code>pip install proxy-requests</code>  (or pip3)
<br>
<code>from proxy_requests import ProxyRequests</code>
<br><br>
or if you need the Basic Auth subclass as well:
<br>
<code>from proxy_requests import ProxyRequests, ProxyRequestsBasicAuth</code>
<br><br>
If the above import statement is used, method calls will be identical to the ones shown below. Pass a fully qualified URL when initializing an instance.
<br><br>
System Requirements: <b>Python 3</b> and the requests module.
<br><br>
Runs on Linux and Windows (and Mac probably) - <b>It may take a moment to run depending on the current proxy.</b>
<br>
Each request with a proxy is set with a 3 second timeout in the event that the request takes too long (before trying the next proxy socket in the queue).
<br><br>
The ProxyRequestBasicAuth subclass has the methods get(), get_with_headers(), post(), post_with_headers(), post_file(), and post_file_with_headers() that will override the Parent methods.
<br>

<b>GET:</b>
<pre>
    <code>
r = ProxyRequests("https://api.ipify.org")
r.get()
    </code>
</pre>

<b>GET with headers:</b>
<pre>
    <code>
h = {"User-Agent": "NCSA Mosaic/3.0 (Windows 95)"}
r = ProxyRequests("url here")
r.set_headers(h)
r.get_with_headers()
    </code>
</pre>

<b>POST:</b>
<pre>
    <code>
r = ProxyRequests("url here")
r.post({"key1": "value1", "key2": "value2"})
    </code>
</pre>

<b>POST with headers:</b>
<pre>
    <code>
r = ProxyRequests("url here")
r.set_headers({"name": "rootVIII", "secret_message": "7Yufs9KIfj33d"})
r.post_with_headers({"key1": "value1", "key2": "value2"})
    </code>
</pre>

<b>POST FILE:</b>
<pre>
    <code>
r = ProxyRequests("url here")
r.set_file({'file': open('test.txt', 'rb')})
r.post_file()
    </code>
</pre>

<b>POST FILE with headers:</b>
<pre>
    <code>
h = {"User-Agent": "NCSA Mosaic/3.0 (Windows 95)"}
r = ProxyRequests("url here")
r.set_headers(h)
r.set_file({'file': open('test.txt', 'rb')})
r.post_file_with_headers()
    </code>
</pre>

<b>GET with Basic Authentication:</b>
<pre>
    <code>
r = ProxyRequestsBasicAuth("url here", "username", "password")
r.get()
    </code>
</pre>

<b>GET with headers & Basic Authentication:</b>
<pre>
    <code>
h = {"User-Agent": "NCSA Mosaic/3.0 (Windows 95)"}
r = ProxyRequestsBasicAuth("url here", "username", "password")
r.set_headers(h)
r.get_with_headers()
    </code>
</pre>

<b>POST with Basic Authentication:</b>
<pre>
    <code>
r = ProxyRequestsBasicAuth("url here", "username", "password")
r.post({"key1": "value1", "key2": "value2"})
    </code>
</pre>

<b>POST with headers & Basic Authentication:</b>
<pre>
    <code>
r = ProxyRequestsBasicAuth("url here", "username", "password")
r.set_headers({"header_key": "header_value"})</code>
r.post_with_headers({"key1": "value1", "key2": "value2"})
    </code>
</pre>

<b>POST FILE with Basic Authentication:</b>
<pre>
    <code>
r = ProxyRequestsBasicAuth("url here", "username", "password")
r.set_file({'file': open('test.txt', 'rb')})
r.post_file()
    </code>
</pre>

<b>POST FILE with headers & Basic Authentication:</b>
<pre>
    <code>
h = {"User-Agent": "NCSA Mosaic/3.0 (Windows 95)"}
r = ProxyRequestsBasicAuth("url here", "username", "password")
r.set_headers(h)</code>
r.set_file({'file': open('test.txt', 'rb')})
r.post_file_with_headers()
    </code>
</pre>    
<br><br>
<strong><u>Response Methods</u></strong>
<br><br>
  <b>Returns a string:</b>
<br>
<code>print(r)</code>
<br>
<b>Or if you want the raw content as bytes: </b>
<br>
<code>r.get_raw()</code>
<br>
<b>Get the response headers:</b>
<br>
<code>print(r.get_headers())</code>
<br>
<b>Get the status code:</b>
<br>
<code>print(r.get_status_code())</code>
<br>
<b>Get the proxy that was used to make the request:</b>
<br>
<code>print(r.get_proxy_used())</code>
<br>
<br>
<b>To write response a to a file (including an image):</b>
<br>
<code>r.response_to_file()</code>
<br>
<b>Load your response to JSON: </b>
<br>
<code>import json</code>
<br>
<code>r = ProxyRequests(url)</code>
<br>
<code>r.get()</code>
<br>
<code>json.loads(r.get_raw().decode())</code>
<br><br>
This was developed on Ubuntu 16.04.4 LTS.
<hr>
<b>Author: James Loye Colley  04AUG2018</b><br><br>
<br>
<img src="https://github.com/rootVIII/proxy_requests/blob/master/ex1.png" alt="example1" height="675" width="950"><hr>
<img src="https://github.com/rootVIII/proxy_requests/blob/master/ex2.png" alt="example1" height="675" width="950"><hr>


import threading
import os
from http.server import BaseHTTPRequestHandler, HTTPServer


class RenderHealthServer(BaseHTTPRequestHandler):
    def do_GET(self):
        self.send_response(200)
        self.send_header("Content-Type", "text/plain")
        self.end_headers()
        self.wfile.write(b"OK")

    def log_message(self, *args):
        pass


def start_render_server():
    try:
        port = int(os.environ.get("PORT", 10000))
        server = HTTPServer(("0.0.0.0", port), RenderHealthServer)
        print(f"Render health server started on port {port}")
        server.serve_forever()
    except Exception as e:
        print(f"Render health server error: {e}")


threading.Thread(target=start_render_server, daemon=True).start()

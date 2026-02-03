# Design
Sustainable Fashion
# app.py
# A simple Flask website on Sustainable Fashion with 5 tabs and 30 content pages
# Run: python app.py  |  Then open http://127.0.0.1:5000

from flask import Flask, render_template_string

app = Flask(__name__)

# Base HTML template
base_template = """
<!DOCTYPE html>
<html lang='en'>
<head>
    <meta charset='UTF-8'>
    <title>{{ title }}</title>
    <style>
        body { font-family: Arial, sans-serif; margin: 0; background:#f4f8f6; }
        header { background:#1b5e20; color:white; padding:20px; text-align:center; }
        nav { background:#2e7d32; padding:10px; text-align:center; }
        nav a { color:white; margin:0 15px; text-decoration:none; font-weight:bold; }
        nav a:hover { text-decoration:underline; }
        .container { padding:30px; }
        h2 { color:#1b5e20; }
        footer { background:#1b5e20; color:white; text-align:center; padding:10px; }
    </style>
</head>
<body>
<header>
    <h1>Sustainable Fashion: Style with a Purpose</h1>
    <p>How conscious clothing choices protect our planet</p>
</header>
<nav>
    <a href='/'>Home</a>
    <a href='/materials'>Materials</a>
    <a href='/production'>Production</a>
    <a href='/consumers'>Consumers</a>
    <a href='/future'>Future</a>
</nav>
<div class='container'>
    {{ content }}
</div>
<footer>
    <p>© 2026 Sustainable Fashion Project</p>
</footer>
</body>
</html>
"""

pages = {
    "home": [
        "Introduction to Sustainable Fashion",
        "Why Fashion Impacts the Environment",
        "Fast Fashion vs Sustainable Fashion",
        "Environmental Cost of Clothing",
        "Climate Change and the Fashion Industry",
        "Water Pollution from Textile Dyes"
    ],
    "materials": [
        "Organic Cotton",
        "Hemp and Linen",
        "Recycled Polyester",
        "Plant-Based Fabrics",
        "Low-Impact Dyes",
        "Biodegradable Textiles"
    ],
    "production": [
        "Ethical Manufacturing",
        "Reducing Carbon Footprint",
        "Energy-Efficient Factories",
        "Fair Wages and Safe Workplaces",
        "Zero-Waste Pattern Making",
        "Local Production Benefits"
    ],
    "consumers": [
        "Mindful Shopping",
        "Capsule Wardrobes",
        "Clothing Care and Longevity",
        "Repair and Reuse Culture",
        "Second-Hand Fashion",
        "Minimalism and Style"
    ],
    "future": [
        "Circular Fashion Economy",
        "Innovations in Sustainable Textiles",
        "Technology in Eco-Fashion",
        "Role of Education",
        "Youth and Sustainable Fashion",
        "A Greener Fashion Future"
    ]
}


def render_page(title, headings):
    content = ""
    for h in headings:
        content += f"<h2>{h}</h2><p>Sustainable fashion focuses on reducing environmental harm by using eco-friendly materials, ethical production methods, and responsible consumption. This topic explains how {h.lower()} contributes to protecting natural resources, reducing pollution, and supporting a healthier planet.</p>"
    return render_template_string(base_template, title=title, content=content)

@app.route('/')
def home():
    return render_page("Home", pages["home"])

@app.route('/materials')
def materials():
    return render_page("Materials", pages["materials"])

@app.route('/production')
def production():
    return render_page("Production", pages["production"])

@app.route('/consumers')
def consumers():
    return render_page("Consumers", pages["consumers"])

@app.route('/future')
def future():
    return render_page("Future", pages["future"])

if __name__ == '__main__':
    app.run(debug=True)

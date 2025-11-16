```jsx name=App.jsx
// Healing Hands Hospital React Component ES Module with Realistic Background, Branding, and Tree

import React, { useState, useEffect } from "https://esm.sh/react";
import {
  Phone, Calendar, Shield, Menu, X
} from "https://esm.sh/lucide-react";

// Realistic, welcoming background example (public domain hospital photo)
const backgroundImage =
  "https://images.unsplash.com/photo-1506744038136-46273834b3fb?auto=format&fit=crop&w=1500&q=80";

const App = () => {
  const [isMenuOpen, setIsMenuOpen] = useState(false);
  const [selectedLanguage, setSelectedLanguage] = useState('English');
  const languages = ['English', 'Spanish', 'French', 'Chinese', 'Arabic'];
  const navigation = [
    { name: 'Home', href: '#home' },
    { name: 'About Us', href: '#about' },
    { name: 'Services', href: '#services' },
    { name: 'Doctors', href: '#doctors' },
    { name: 'Emergency', href: '#emergency' },
    { name: 'Resources', href: '#resources' },
    { name: 'Contact', href: '#contact' }
  ];

  useEffect(() => {
    const savedLanguage = localStorage.getItem('preferredLanguage');
    if (savedLanguage) setSelectedLanguage(savedLanguage);
  }, []);

  return (
    <div className="min-h-screen relative bg-gray-50 overflow-hidden">
      {/* Background image -- blurred and shaded, coded for realism */}
      <div
        className="absolute inset-0 -z-10"
        style={{
          backgroundImage: `url('${backgroundImage}')`,
          backgroundSize: "cover",
          backgroundPosition: "center",
          filter: "blur(2px) brightness(0.7)"
        }}>
      </div>
      {/* Color overlay: blue + green gradients for hospital/nature feel */}
      <div className="absolute inset-0 bg-gradient-to-b from-blue-900/60 to-green-500/30 -z-10"></div>
      {/* Tree illustration in the corner for a "nature/condusive" theme */}
      <div className="absolute bottom-0 right-0 max-w-xs opacity-75 pointer-events-none" style={{zIndex: 0}}>
        <img src="https://www.svgrepo.com/show/12820/tree.svg" alt="Tree" style={{width:150, height:'auto'}} />
      </div>

      {/* Header */}
      <header className="bg-white/90 shadow-sm sticky top-0 z-50 rounded-b-3xl">
        <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
          <div className="flex justify-between items-center h-16">
            {/* Logo + Name in prominent box */}
            <div className="flex items-center space-x-3">
              <Shield className="h-8 w-8 text-blue-600" />
              <span className="text-2xl font-extrabold text-blue-900 drop-shadow-sm bg-white/80 px-3 py-1 rounded-xl">Healing Hands Hospital</span>
            </div>
            <nav className="hidden md:flex items-center space-x-8">
              {navigation.map(item => (
                <a key={item.name} href={item.href} className="text-gray-700 hover:text-blue-600 font-medium">
                  {item.name}
                </a>
              ))}
              <select
                value={selectedLanguage}
                onChange={e => setSelectedLanguage(e.target.value)}
                className="border border-gray-300 rounded-md px-2 py-1 text-sm focus:outline-none focus:ring-2 focus:ring-blue-500"
              >
                {languages.map(lang => (
                  <option key={lang} value={lang}>{lang}</option>
                ))}
              </select>
            </nav>
            <div className="hidden md:flex items-center space-x-4">
              <button className="bg-red-600 text-white px-4 py-2 rounded-lg flex items-center">
                <Phone className="h-4 w-4 mr-2" /> Emergency: 911
              </button>
              <button className="bg-blue-600 text-white px-4 py-2 rounded-lg flex items-center">
                <Calendar className="h-4 w-4 mr-2" /> Schedule Appointment
              </button>
            </div>
            <button
              onClick={() => setIsMenuOpen(!isMenuOpen)}
              className="md:hidden p-2 rounded-md text-gray-700 hover:text-blue-600"
            >
              {isMenuOpen ? <X className="h-6 w-6"/> : <Menu className="h-6 w-6"/>}
            </button>
          </div>
        </div>
        {/* Mobile Menu */}
        {isMenuOpen && (
          <div className="md:hidden bg-white border-t">
            <div className="px-4 py-2 space-y-2">
              {navigation.map(item => (
                <a key={item.name} href={item.href} className="block py-2 text-gray-700 hover:text-blue-600" onClick={()=>setIsMenuOpen(false)}>{item.name}</a>
              ))}
              <div className="pt-4 border-t">
                <select
                  value={selectedLanguage}
                  onChange={e => setSelectedLanguage(e.target.value)}
                  className="w-full border border-gray-300 rounded-md px-3 py-2 text-sm focus:outline-none focus:ring-2 focus:ring-blue-500"
                >
                  {languages.map(lang => (
                    <option key={lang} value={lang}>{lang}</option>
                  ))}
                </select>
              </div>
            </div>
          </div>
        )}
      </header>

      {/* Hero Section */}
      <section id="home" className="py-24 flex items-center justify-center">
        <div className="max-w-3xl w-full mx-auto bg-white/80 rounded-3xl shadow-xl p-10 text-center flex flex-col items-center backdrop-blur-2xl" style={{zIndex:1}}>
          <Shield className="h-12 w-12 mx-auto text-blue-600 mb-4" />
          <h1 className="text-4xl md:text-5xl font-extrabold mb-4 text-blue-900 drop-shadow-md">
            Healing Hands Hospital
          </h1>
          <p className="text-lg mb-4 text-gray-700 font-medium">
            Compassionate Care, Exceptional Outcomes
          </p>
          <p className="text-base mb-8 text-gray-600">
            Serving our community for over 50 years. Experience world-class medical care in a healing, green environment.
          </p>
          <div className="flex flex-col sm:flex-row gap-4 justify-center mt-4">
            <button className="bg-blue-600 text-white px-8 py-4 rounded-lg font-semibold flex items-center shadow hover:bg-blue-700">
              <Calendar className="h-5 w-5 mr-2" /> Schedule Appointment
            </button>
            <button className="bg-red-600 text-white px-8 py-4 rounded-lg font-semibold flex items-center shadow hover:bg-red-700">
              <Phone className="h-5 w-5 mr-2" /> Emergency: 911
            </button>
          </div>
        </div>
      </section>
      {/* Footer Section */}
      <footer className="bg-gray-800/70 text-white py-10 mt-20">
        <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
          <h2 className="text-2xl mb-6">Get in Touch</h2>
          <div className="flex justify-center gap-6">
            <button className="bg-red-600 text-white px-6 py-3 rounded-lg hover:bg-red-700 flex items-center">
              <Phone className="h-5 w-5 mr-2" /> Emergency: 911
            </button>
            <button className="bg-blue-600 text-white px-6 py-3 rounded-lg hover:bg-blue-700 flex items-center">
              <Calendar className="h-5 w-5 mr-2" /> Schedule Appointment
            </button>
          </div>
        </div>
      </footer>
    </div>
  );
};

export default App;
```

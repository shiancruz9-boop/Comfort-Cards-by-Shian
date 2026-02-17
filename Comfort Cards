import React, { useState, useEffect } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { motion, AnimatePresence } from "framer-motion";
import { Heart, Sparkles, RefreshCw, MessageCircle, Share2 } from "lucide-react";
import { Helmet } from "react-helmet";

const comfortCards = [
  { id: 1, type: "quote", title: "Ginagawa Mo Ang Kaya Mo", message: "Kahit mabigat ang araw, patuloy ka pa ring lumalaban. Sapat na iyon." },
  { id: 2, type: "quote", title: "Lilipas Din Ito", message: "Walang permanenteng hirap. Nalagpasan mo ang lahat ng nakaraan â€” malalagpasan mo rin ito." },
  { id: 3, type: "quote", title: "Karapat-dapat Kang Magpahinga", message: "Ang pahinga ay hindi katamaran. Ito ay paraan para gumaling at lumakas." },
  { id: 4, type: "quote", title: "Importante Ka", message: "May halaga ang presensya mo kahit hindi mo ito nakikita ngayon." },
  { id: 5, type: "quote", title: "Isang Hakbang Lang", message: "Hindi mo kailangang ayusin ang lahat ngayon. Isang maliit na hakbang ay sapat." },
  { id: 6, type: "quote", title: "Hindi Ka Nag-iisa", message: "May mga taong nagmamalasakit sa'yo at gustong maging okay ka." },
  { id: 7, type: "quote", title: "Okay Lang Hindi Maging Okay", message: "Hindi mo kailangang maging malakas palagi. Tao ka lang." },
  { id: 8, type: "quote", title: "May Bagong Bukas", message: "Kahit pangit ang araw ngayon, may chance ulit bukas." },
  { id: 9, type: "question", title: "Self Check", message: "Kumain ka na ba ngayon?" },
  { id: 10, type: "question", title: "Self Check", message: "Uminom ka na ba ng tubig?" },
  { id: 11, type: "question", title: "Self Check", message: "Nakakapagpahinga ka ba nang maayos?" },
  { id: 12, type: "question", title: "Reflection", message: "Ano ang isang bagay na kinaya mo ngayong araw?" },
  { id: 13, type: "question", title: "Reflection", message: "May taong pwede mong makausap ngayon?" },
  { id: 14, type: "question", title: "Reflection", message: "Ano ang isang maliit na bagay na nagpapasaya sa'yo?" },
];

function getRandomCard() {
  return comfortCards[Math.floor(Math.random() * comfortCards.length)];
}

export default function ComfortCardsApp() {
  const [card, setCard] = useState(getRandomCard());

  useEffect(() => {
    setCard(getRandomCard());
  }, []);

  const newRandomCard = () => {
    setCard(getRandomCard());
  };

  const shareApp = async () => {
    const shareData = {
      title: "Comfort Cards",
      text: "Para sa'yo â€” random comfort message ðŸ’™",
      url: window.location.href,
    };

    try {
      if (navigator.share) {
        await navigator.share(shareData);
      } else {
        await navigator.clipboard.writeText(window.location.href);
        alert("Link copied! Pwede mo na i-send.");
      }
    } catch (err) {
      console.log(err);
    }
  };

  const previewTitle = "Comfort Cards Para Sa'yo ðŸ’™";
  const previewDesc = "Buksan mo ito para sa random comfort quote o question.";
  const previewImage = "https://images.unsplash.com/photo-1516589178581-6cd7833ae3b2";

  return (
    <>
      <Helmet>
        <title>{previewTitle}</title>

        <meta property="og:title" content={previewTitle} />
        <meta property="og:description" content={previewDesc} />
        <meta property="og:image" content={previewImage} />
        <meta property="og:type" content="website" />

        <meta name="twitter:card" content="summary_large_image" />
        <meta name="twitter:title" content={previewTitle} />
        <meta name="twitter:description" content={previewDesc} />
        <meta name="twitter:image" content={previewImage} />
      </Helmet>

      <div className="min-h-screen bg-gradient-to-br from-slate-50 to-slate-200 flex items-center justify-center p-6">
        <div className="max-w-md w-full space-y-6">
          <div className="text-center space-y-2">
            <h1 className="text-3xl font-bold tracking-tight flex items-center justify-center gap-2">
              <Heart className="w-7 h-7" /> Comfort Cards
            </h1>
            <p className="text-sm text-muted-foreground">
              Pindutin ang button kapag kailangan mo ng kaunting lakas ng loob.
            </p>
          </div>

          <AnimatePresence mode="wait">
            <motion.div
              key={card.id}
              initial={{ opacity: 0, y: 30 }}
              animate={{ opacity: 1, y: 0 }}
              exit={{ opacity: 0, y: -30 }}
              transition={{ duration: 0.4 }}
            >
              <Card className="rounded-2xl shadow-lg">
                <CardContent className="p-8 space-y-4 text-center">
                  {card.type === "quote" ? (
                    <Sparkles className="w-6 h-6 mx-auto" />
                  ) : (
                    <MessageCircle className="w-6 h-6 mx-auto" />
                  )}

                  <h2 className="text-xl font-semibold">{card.title}</h2>
                  <p className="text-base text-muted-foreground">{card.message}</p>
                </CardContent>
              </Card>
            </motion.div>
          </AnimatePresence>

          <div className="flex gap-3">
            <Button className="flex-1 rounded-2xl text-base py-6" onClick={newRandomCard}>
              <RefreshCw className="w-4 h-4 mr-2" />
              Bagong Card
            </Button>

            <Button className="rounded-2xl px-6" onClick={shareApp}>
              <Share2 className="w-4 h-4" />
            </Button>
          </div>
        </div>
      </div>
    </>
  );
}

import * as React from "react"
import { useState } from "react"
import { addPropertyControls, ControlType } from "framer"

/**
 * ProjectCard
 * A project summary card for a Framer site. Clicking it opens the 3D viewer
 * (model + threaded, role-tagged comments) in a modal popup via an iframe.
 *
 * IMPORTANT: this version loads the viewer from a URL (the `viewerUrl` prop)
 * rather than embedding it inline. Embedding the full viewer's HTML directly
 * in this file made it too large (~1.3MB in one giant string) for Framer's
 * code editor/build pipeline to handle reliably. Host the exported
 * `3d-viewer-prototype.html` file somewhere with a public URL (e.g. GitHub
 * Pages, Netlify, Vercel, or your own server) and paste that URL into the
 * "Viewer URL" property control in Framer.
 *
 * @framerSupportedLayoutWidth any
 * @framerSupportedLayoutHeight any
 */
export default function ProjectCard(props) {
    const {
        title,
        rfqNumber,
        buyerName,
        description,
        accentColor,
        thumbnailEmoji,
        viewerUrl,
    } = props

    const [open, setOpen] = useState(false)

    return (
        <>
            <div
                onClick={() => setOpen(true)}
                style={{
                    display: "flex",
                    flexDirection: "column",
                    width: "100%",
                    height: "100%",
                    background: "#FFFFFF",
                    borderRadius: 12,
                    overflow: "hidden",
                    cursor: "pointer",
                    boxShadow: "0px 1px 3px rgba(0,0,0,0.12)",
                    border: "1px solid #E4E8EC",
                    fontFamily:
                        "'Inter', -apple-system, BlinkMacSystemFont, sans-serif",
                    transition: "box-shadow 0.15s ease, transform 0.15s ease",
                }}
                onMouseEnter={(e) => {
                    e.currentTarget.style.boxShadow =
                        "0px 6px 20px rgba(0,0,0,0.14)"
                    e.currentTarget.style.transform = "translateY(-2px)"
                }}
                onMouseLeave={(e) => {
                    e.currentTarget.style.boxShadow =
                        "0px 1px 3px rgba(0,0,0,0.12)"
                    e.currentTarget.style.transform = "translateY(0)"
                }}
            >
                <div
                    style={{
                        height: 120,
                        flexShrink: 0,
                        display: "flex",
                        alignItems: "center",
                        justifyContent: "center",
                        fontSize: 40,
                        background: `linear-gradient(135deg, ${accentColor}22, ${accentColor}0D)`,
                    }}
                >
                    {thumbnailEmoji}
                </div>
                <div
                    style={{
                        padding: "14px 16px 16px",
                        display: "flex",
                        flexDirection: "column",
                        gap: 6,
                        flex: 1,
                    }}
                >
                    <div
                        style={{
                            fontSize: 15,
                            fontWeight: 700,
                            color: "#1F2933",
                        }}
                    >
                        {title}
                    </div>
                    <div
                        style={{
                            fontSize: 11,
                            fontWeight: 600,
                            color: accentColor,
                        }}
                    >
                        RFQ #{rfqNumber} · {buyerName}
                    </div>
                    <div
                        style={{
                            fontSize: 12,
                            lineHeight: 1.4,
                            color: "#697786",
                            marginTop: 2,
                        }}
                    >
                        {description}
                    </div>
                    <div
                        style={{
                            marginTop: "auto",
                            paddingTop: 10,
                            fontSize: 11,
                            fontWeight: 600,
                            color: accentColor,
                            display: "flex",
                            alignItems: "center",
                            gap: 4,
                        }}
                    >
                        Open 3D viewer →
                    </div>
                </div>
            </div>

            {open && (
                <div
                    onClick={() => setOpen(false)}
                    style={{
                        position: "fixed",
                        inset: 0,
                        background: "rgba(20,24,31,0.6)",
                        display: "flex",
                        alignItems: "center",
                        justifyContent: "center",
                        zIndex: 9999,
                    }}
                >
                    <div
                        onClick={(e) => e.stopPropagation()}
                        style={{
                            position: "relative",
                            width: "95vw",
                            maxWidth: 1500,
                            height: "90vh",
                            borderRadius: 16,
                            overflow: "hidden",
                            boxShadow: "0 24px 64px rgba(0,0,0,0.4)",
                        }}
                    >
                        <button
                            onClick={() => setOpen(false)}
                            aria-label="Close"
                            style={{
                                position: "absolute",
                                top: -14,
                                right: -14,
                                width: 32,
                                height: 32,
                                borderRadius: "50%",
                                border: "none",
                                background: "#fff",
                                boxShadow: "0px 0px 4px rgba(0,0,0,0.16)",
                                display: "flex",
                                alignItems: "center",
                                justifyContent: "center",
                                cursor: "pointer",
                                zIndex: 10,
                                fontSize: 16,
                                color: "#546881",
                            }}
                        >
                            ✕
                        </button>
                        {viewerUrl ? (
                            <iframe
                                title="3D Viewer"
                                src={viewerUrl}
                                style={{
                                    width: "100%",
                                    height: "100%",
                                    border: "none",
                                    borderRadius: 16,
                                    background: "#F6F8F9",
                                }}
                            />
                        ) : (
                            <div
                                style={{
                                    width: "100%",
                                    height: "100%",
                                    background: "#F6F8F9",
                                    display: "flex",
                                    alignItems: "center",
                                    justifyContent: "center",
                                    fontFamily: "'Inter', sans-serif",
                                    color: "#697786",
                                    fontSize: 13,
                                    textAlign: "center",
                                    padding: 40,
                                }}
                            >
                                Set the "Viewer URL" property to your hosted
                                3d-viewer-prototype.html to load it here.
                            </div>
                        )}
                    </div>
                </div>
            )}
        </>
    )
}

ProjectCard.defaultProps = {
    title: "Money Man",
    rfqNumber: "24815",
    buyerName: "Ascension Manufacturing",
    description:
        "Interactive 3D review with pinned, threaded comments for buyer/manufacturer collaboration.",
    accentColor: "#7636D9",
    thumbnailEmoji: "🎩",
    viewerUrl: "",
}

addPropertyControls(ProjectCard, {
    title: { type: ControlType.String, title: "Title", defaultValue: "Money Man" },
    rfqNumber: { type: ControlType.String, title: "RFQ #", defaultValue: "24815" },
    buyerName: {
        type: ControlType.String,
        title: "Buyer",
        defaultValue: "Ascension Manufacturing",
    },
    description: {
        type: ControlType.String,
        title: "Description",
        defaultValue:
            "Interactive 3D review with pinned, threaded comments for buyer/manufacturer collaboration.",
        displayTextArea: true,
    },
    accentColor: {
        type: ControlType.Color,
        title: "Accent",
        defaultValue: "#7636D9",
    },
    thumbnailEmoji: {
        type: ControlType.String,
        title: "Thumbnail Icon",
        defaultValue: "🎩",
    },
    viewerUrl: {
        type: ControlType.String,
        title: "Viewer URL",
        placeholder: "https://your-host.com/3d-viewer-prototype.html",
        defaultValue: "",
    },
})
